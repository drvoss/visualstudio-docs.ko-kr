---
title: 로컬 속성 가져오기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, getting local properties
- debugging [Debugging SDK], local properties
- expression evaluation, local properties
ms.assetid: 6c3a79e8-1ba1-4863-97c3-0216c3d9f092
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c10cd5ebfe1efbf6657b9925c4c27cce33591524
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338265"
---
# <a name="get-local-properties"></a>로컬 속성 가져오기
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

Visual Studio 호출 [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) 가져오려고는 [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) 에 표시 되는 모든 지역에 대 한 액세스를 제공 하는 개체를 **지역** 창입니다. Visual Studio 호출 [다음](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) 각 로컬에 대해 표시할 정보를 가져옵니다. 이 예제에서는 클래스 `CEnumPropertyInfo` 구현 된 `IEnumDebugPropertyInfo2` 인터페이스입니다.

이 구현의 `IEnumDebugPropertyInfo2::Next` 다음 작업을 수행 합니다.

1. 정보를 저장할 배열입니다를 지웁니다.

2. 호출 [다음](../../extensibility/debugger/reference/ienumdebugfields-next.md) 각 로컬 저장 반환 된 [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) 반환할 배열의 합니다. 합니다 [IEnumDebugFields](../../extensibility/debugger/reference/ienumdebugfields.md) 개체가 제공 된 경우이 `CEnumPropertyInfo` 클래스 인스턴스화 되었습니다.

## <a name="managed-code"></a>관리 코드
이 예제에서는 구현을 보여 줍니다. `IEnumDebugPropertyInfo2::EnumChildren` 관리 코드에서 메서드의 지역에 대 한 합니다.

```csharp
namespace EEMC
{
    public class CEnumMethodField : IEnumDebugFields
    {
        public HRESULT Next(
                uint                  count,
                DEBUG_PROPERTY_INFO[] properties,
            out uint                  fetched)
        {
            if (count > properties.Length)
                throw new COMException();

            // Zero out the array.
            for (int i= 0; i < count; i++)
            {
                properties[i].bstrFullName = "";
                properties[i].bstrName = "";
                properties[i].bstrType = "";
                properties[i].bstrValue = "";
                properties[i].dwAttrib = 0;
                properties[i].dwFields = 0;
                properties[i].pProperty = null;
            }
            fetched = 0;

            // COM interop.
            HRESULT hr;
            uint innerFetched;
            IDebugField[] field = new IDebugField[1];

            while (fetched < count)
            {
                field[0] = null;
                innerFetched = 0;

                // Get next field.
                if (fetched < fieldCount)
                    hr = fields.Next(1, field, ref innerFetched);
                // No more fields.
                else return COM.S_FALSE;

                if (hr != COM.S_OK || innerFetched != 1 || field[0] == null)
                    throw new COMException("CEnumPropertyInfo.Next");

                // Get property from field.
                CFieldProperty fieldProperty =
                        new CFieldProperty(provider, address, binder, field[0]);

                DEBUG_PROPERTY_INFO[] property =
                        new DEBUG_PROPERTY_INFO[1];
                fieldProperty.GetPropertyInfo((uint) infoFlags, radix, 0, null, 0, property);
                properties[fetched++] = property[0];
            }
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>관리 되지 않는 코드
 이 예제에서는 구현을 보여 줍니다. `IEnumDebugPropertyInfo2::EnumChildren` 비관리 코드에서 메서드의 지역에 대 한 합니다.

```cpp
STDMETHODIMP CEnumPropertyInfo::Next(
    in  ULONG                count,
    out DEBUG_PROPERTY_INFO* pelements,
    out ULONG*               pfetched )
{
    if (pfetched)
        *pfetched = 0;
    if (!pelements)
        return E_INVALIDARG;
    else
        memset( pelements, 0, count * sizeof(DEBUG_PROPERTY_INFO));

    HRESULT hr  = S_OK;
    ULONG   idx = 0;
    while (idx < count)
    {
        ULONG        fetchedFields;
        IDebugField* pfield;

        //get the next field
        hr = m_fields->Next( 1, &pfield, &fetchedFields );
        if (FAILED(hr))
            return hr;
        if (fetchedFields != 1)
            return E_FAIL;
        idx++;

        //create a CFieldProperty to retrieve the DEBUG_PROPERTY_INFO
        CFieldProperty* pproperty =
            new CFieldProperty( m_provider, m_address, m_binder, pfield );
        pfield->Release();
        if (!pproperty)
            return E_OUTOFMEMORY;

        hr = pproperty->Init();
        if (FAILED(hr))
        {
            pproperty->Release();
            return hr;
        }

        hr = pproperty->GetPropertyInfo( m_infoFlags,
                                         m_radix,
                                         0,
                                         NULL,
                                         0,
                                         pelements + idx - 1);
        pproperty->Release();
        if (FAILED(hr))
            return hr;
    }

    if (pfetched)
        *pfetched = idx;
    return hr;
}
```

## <a name="see-also"></a>참고자료
- [지역 변수의 샘플 구현](../../extensibility/debugger/sample-implementation-of-locals.md)
- [로컬 항목 열거](../../extensibility/debugger/enumerating-locals.md)
