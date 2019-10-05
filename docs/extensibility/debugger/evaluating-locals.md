---
title: 지역 변수를 계산 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], evaluating locals
- expression evaluation, evaluating locals
ms.assetid: 7d1ed528-4e7a-4d8f-87b4-162440644a75
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed43dae7aaf2fe7c130f6822a46ce429661634ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315410"
---
# <a name="evaluate-locals"></a>지역 변수를 평가 합니다.
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 내용은 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

[GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) 로컬 뿐만 아니라 지역 변수의 이름 및 형식 값을 얻기 위해 호출 됩니다. 로컬 값 프로그램의 현재 상태에 종속 되므로 메모리에서 지역 변수의 값을 얻어야 합니다. 합니다 [IDebugBinder](../../extensibility/debugger/reference/idebugbinder.md) 개체는 바인딩하는 데 사용 되는 [IDebugField](../../extensibility/debugger/reference/idebugfield.md) 로컬 값을 포함 하는 메모리에서 해당 위치를 나타내는 개체입니다. 메모리에서이 위치에서 표시 됩니다는 [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) 개체입니다.

이 기능은 로컬 값을 검색 하는 다음 작업을 수행 하는 도우미 함수에 캡슐화 됩니다.

1. 바인딩하는 `IDebugField` 메모리를 얻으려고 하는 개체는 `IDebugObject` 개체입니다.

2. 메모리에서 값을 가져옵니다. 이 값은 일련의 바이트로로 표시 됩니다.

3. 지역 변수의 형식을 기반으로 값 형식을 지정 합니다.

4. 지역 변수의 값을 포함 하는 일반 개체를 반환 합니다. C#,이 `object`, 및 C++,이 `VARIANT`합니다.

## <a name="managed-code"></a>관리 코드
 관리 코드에서 로컬 변수의 값을 검색 하는 함수는 구현입니다.

```csharp
namespace EEMC
{
    internal class Field
    {
        internal static object GetValue(
            IDebugBinder binder,
            IDebugField field,
            Type t,
            uint size)
        {
            if (t == null || size == 0)  return null;

            IDebugObject debugObject = null;
            binder.Bind(null, field, out debugObject);

            byte[] buffer = new byte[size];
            for (int i = 0; i < size; i++)  buffer[i] = 0;

            debugObject.GetValue(buffer, size);

            if (t == typeof(sbyte)) return (sbyte) buffer[0];
            if (t == typeof(short)) return BitConverter.ToInt16(buffer, 0);
            if (t == typeof(int))   return BitConverter.ToInt32(buffer, 0);
            if (t == typeof(long))  return BitConverter.ToInt64(buffer, 0);
            if (t == typeof(byte))  return buffer[0];
            if (t == typeof(char))  return BitConverter.ToChar(buffer, 0);
            if (t == typeof(uint))  return BitConverter.ToUInt32(buffer, 0);
            if (t == typeof(ulong)) return BitConverter.ToUInt64(buffer, 0);
            if (t == typeof(float)) return BitConverter.ToSingle(buffer, 0);
            if (t == typeof(double))  return BitConverter.ToDouble(buffer, 0);
            if (t == typeof(bool))  return BitConverter.ToBoolean(buffer, 0);
            if (t == typeof(string))  return BitConverter.ToString(buffer, 0);
            return null;
        }
    }
}
```

## <a name="unmanaged-code"></a>관리 되지 않는 코드
 비관리 코드에서 로컬 변수의 값을 검색 하는 함수는 구현입니다. `FieldGetType` 에 표시 됩니다 [로컬 값 가져오기](../../extensibility/debugger/getting-local-values.md)합니다.

```cpp
HRESULT FieldGetPrimitiveValue(
    in  IDebugBinder* pbinder,
    in  IDebugField*  pfield,
    out VARIANT*      pvarValue
    )
{
    if (pvarValue == NULL)
        return E_INVALIDARG;
    else
        *pvarValue = 0;

    if (pfield == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    UINT          valueSize = 0;
    BYTE*         pvalueBits = NULL;
    IDebugObject* pobject    = NULL;

    //get the value as bits
    hr = pbinder->Bind( NULL, pfield, &pobject );
    if (FAILED(hr))
        return hr;

    hr = pobject->GetSize( &valueSize );
    if (FAILED(hr))
    {
        pobject->Release();
        return hr;
    }

    pvalueBits = reinterpret_cast<BYTE *>(malloc(valueSize * sizeof(BYTE)));
    if (!pvalueBits)
    {
        pobject->Release();
        return E_OUTOFMEMORY;
    }

    hr = pobject->GetValue( pvalueBits, valueSize );
    pobject->Release();
    if (FAILED(hr))
    {
        free(pvalueBits);
        return hr;
    }

    //get the type
    VARIANT     valueType;

    hr = FieldGetType( pfield, &valueType );
    if (FAILED(hr))
    {
        free(pvalueBits);
        return hr;
    }

    //copy a primitive value
    switch (valueType.vt)
    {
    case VT_BSTR:
        {
            pvarValue->vt = VT_BSTR;
            if (valueSize == 0)
                pvarValue->bstrVal = SysAllocString( OLE("") );
            else
                pvarValue->bstrVal =
                    SysAllocStringByteLen( reinterpret_cast<char*>(pvalueBits),
                                           valueSize );
        }

    case VT_BOOL:
    case VT_I1:
    case VT_I2:
    case VT_I4:
    case VT_I8:
    case VT_UI1:
    case VT_UI2:
    case VT_UI4:
    case VT_UI8:
    case VT_R4:
    case VT_R8:
        pvarValue->vt = valueType.vt;

        if (valueSize > 8)
            valueSize = 8;
        memcpy( &(pvarValue->iVal), pvalueBits, valueSize );
        break;

    case VT_VOID:
    case VT_EMPTY:
        pvarValue->vt = valueType.vt;
        break;

    default:
        //not a primitive type
        VariantClear(&valueType);
        free(pvalueBits);
        return E_FAIL;
    }

    free(pvalueBits);
    VariantClear(&valueType);
    return S_OK;
}
```

## <a name="see-also"></a>참고자료
- [지역 변수의 샘플 구현](../../extensibility/debugger/sample-implementation-of-locals.md)
- [로컬 값을 얻으려면](../../extensibility/debugger/getting-local-values.md)
- [평가 컨텍스트](../../extensibility/debugger/evaluation-context.md)
