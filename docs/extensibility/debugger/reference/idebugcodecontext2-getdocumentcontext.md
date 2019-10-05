---
title: IDebugCodeContext2::GetDocumentContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCodeContext2::GetDocumentContext
helpviewer_keywords:
- IDebugCodeContext2::GetDocumentContext
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a12838db0687fd7ebe20a5c576db0e06ece49107
ms.sourcegitcommit: 34807a6b6105ae7839adde8ff994c85182ad3aff
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2019
ms.locfileid: "67342403"
---
# <a name="idebugcodecontext2getdocumentcontext"></a>IDebugCodeContext2::GetDocumentContext
이 코드 컨텍스트에 해당 하는 문서 컨텍스트를 가져옵니다. 문서 컨텍스트를이 명령 생성 된 소스 코드에 해당 하는 소스 파일의 위치를 나타냅니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDocumentContext( 
   IDebugDocumentContext2** ppSrcCxt
);
```

```csharp
int GetDocumentContext( 
   out IDebugDocumentContext2 ppSrcCxt
);
```

## <a name="parameters"></a>매개 변수
`ppSrcCxt`\
[out] 반환 된 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 코드 컨텍스트에 해당 하는 개체입니다. 하는 경우 `S_OK` 반환 되 면 동안의 해야 이외`null`합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 디버그 엔진을 반환할지 오류 코드와 같은 `E_FAIL` 때 합니다 `out` 매개 변수는 `null` 코드 컨텍스트에 없는 연결 된 소스 위치를에 하는 경우와 같이 합니다.

## <a name="remarks"></a>설명
 일반적으로 문서 컨텍스트를 생각할 수 있습니다 소스 파일의 위치와 코드 컨텍스트는 실행 스트림에 코드 명령의 위치입니다.

## <a name="see-also"></a>참고자료
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
