---
title: IDebugDocumentContext2::GetName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d968a908a43b215162a46cea7d9e0251ff40d431
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349126"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
이 문서 컨텍스트를 포함 하는 문서의 표시할 수 있는 이름을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetName(
    GETNAME_TYPE gnType,
    BSTR*        pbstrFileName
);
```

```csharp
int GetName(
    enum_GETNAME_TYPE  gnType,
    out string         pbstrFileName
);
```

## <a name="parameters"></a>매개 변수
`gnType`\
[in] 값을 [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) 반환할 이름의 형식을 지정 하는 열거형입니다.

`pbstrFileName`\
[out] 파일의 이름을 반환합니다.

## <a name="return-value"></a>반환 값
성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
이 메서드는 일반적으로 호출을 전달 합니다 [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) 메서드 (예제에서는 표시)으로 문서 이름 자체를 저장할 문서 컨텍스트 기록 않으면.

## <a name="example"></a>예제
다음 예제에서는 간단한에 대 한이 메서드를 구현 하는 방법을 보여 줍니다 `CDebugContext` 노출 하는 개체를 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 인터페이스입니다.

```cpp
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)
{
    HRESULT hr;

    // Check for a valid file name argument.
    if (pbstrFileName)
    {
        *pbstrFileName = NULL;

        switch (gnType)
        {
            case GN_NAME:
            case GN_FILENAME:
            {
                // Copy the member file name into the local file name.
                *pbstrFileName = SysAllocString(m_sbstrFileName);
                // Check for successful copy.
                hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;
                break;
            }
            default:
            {
                hr = E_FAIL;
                break;
            }
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>참고자료
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
