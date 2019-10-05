---
title: CONTEXT_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6c50d5ea930f05d22b68416978909cceca17727d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346459"
---
# <a name="contextinfo"></a>CONTEXT_INFO
이 구조는 메모리 컨텍스트 또는 코드 컨텍스트를 설명합니다.

## <a name="syntax"></a>구문

```cpp
typedef struct _tagCONTEXT_INFO {
    CONTEXT_INFO_FIELDS dwFields;
    BSTR                bstrModuleUrl;
    BSTR                bstrFunction;
    TEXT_POSITION       posFunctionOffset;
    BSTR                bstrAddress;
    BSTR                bstrAddressOffset;
    BSTR                bstrAddressAbsolute;
} CONTEXT_INFO;
```

```csharp
public struct CONTEXT_INFO {
    public uint          dwFields;
    public string        bstrModuleUrl;
    public string        bstrFunction;
    public TEXT_POSITION posFunctionOffset;
    public string        bstrAddress;
    public string        bstrAddressOffset;
    public string        bstrAddressAbsolute;
};
```

## <a name="members"></a>멤버
`dwFields`\
그의 플래그의 조합을 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) 채워진 필드를 지정 하는 열거형<strong>합니다.</strong>

`bstrModuleUrl`\
컨텍스트가 있는 모듈의 이름입니다.

`bstrFunction`\
컨텍스트가 있는 함수 이름입니다.

`posFunctionOffset`\
A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 코드 컨텍스트와 연결 된 함수의 줄 및 열 오프셋을 식별 하는 구조입니다.

`bstrAddress`\
지정된 된 컨텍스트 위치한 코드 주소입니다.

`bstrAddressOffset`\
지정된 된 컨텍스트 위치한 코드에서 주소의 오프셋입니다.

`bstrAddressAbsolute`\
지정 된 컨텍스트가 있는 메모리의 절대 주소입니다.

## <a name="remarks"></a>설명
이 구조에 대 한 호출에서 반환 되는 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) 메서드.

이 구조에 대 한 일반적인 용도 지 원하는 것을 **메모리** 디버그 창입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [클래스 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
- [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
