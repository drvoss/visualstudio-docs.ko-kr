---
title: IDebugDisassemblyStream2::GetCodeLocationId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
helpviewer_keywords:
- IDebugDisassemblyStream2::GetCodeLocationId
ms.assetid: 567adfb8-2f54-499a-a027-e4ecb82277ef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 58e3b12ecbc75b7d07d60ac399412dc5b0deb73b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351691"
---
# <a name="idebugdisassemblystream2getcodelocationid"></a>IDebugDisassemblyStream2::GetCodeLocationId
특정 코드 컨텍스트에 대 한 코드 위치 식별자를 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCodeLocationId( 
   IDebugCodeContext2* pCodeContext,
   UINT64*             puCodeLocationId
);
```

```csharp
int GetCodeLocationId( 
   IDebugCodeContext2 pCodeContext,
   out ulong          puCodeLocationId
);
```

## <a name="parameters"></a>매개 변수
`pCodeContext`\
[in] [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) 식별자로 변환 될 개체입니다.

`puCodeLocationId` [out] 코드 위치 식별자를 반환합니다. 설명 부분을 참조하세요.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 반환 `E_CODE_CONTEXT_OUT_OF_SCOPE` 코드 컨텍스트에 유효 하지만 범위 밖에 있습니다.

## <a name="remarks"></a>설명
 코드 위치 식별자 디스어셈블리를 지 원하는 디버그 엔진 (DE)와 관련이 있습니다. 이 위치 식별자 코드의 위치를 추적 하는 DE에서 내부적으로 사용 및는 일반적으로 주소 또는 일종의 오프셋입니다. 유일한 요구 사항은 한 위치의 코드 컨텍스트를 사용 하면 다른 위치의 코드 컨텍스트 보다 작으면 첫 번째 코드 컨텍스트에서의 해당 코드 위치 식별자도 보다 작아야 두 번째 코드 컨텍스트의 코드 위치 식별자를 합니다.

 코드 위치 식별자의 코드 컨텍스트를 검색 하려면 호출을 [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md) 메서드.

## <a name="see-also"></a>참고자료
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)