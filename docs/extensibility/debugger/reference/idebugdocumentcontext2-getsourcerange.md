---
title: IDebugDocumentContext2::GetSourceRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 210ac493a2b717b901e989dcb248efe29ad3fe75
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311851"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
이 문서 컨텍스트의 소스 코드 범위를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSourceRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetSourceRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>매개 변수
`pBegPosition`\
[out에서] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조 시작 위치를 사용 하 여 입력 됩니다. 이 정보가 필요 하지 않은 경우이 인수를 null 값으로 설정 합니다.

`pEndPosition`\
[out에서] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조 끝 위치를 사용 하 여 입력 됩니다. 이 정보가 필요 하지 않은 경우이 인수를 null 값으로 설정 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 소스 범위는 소스 코드에서 바로 코드를 제공 하는 이전 문을 후 현재 문 다시의 전체 범위가입니다. 소스 범위에는 일반적으로 주석, 디스어셈블리 창에서 코드를 포함 하 여 원본 문을 혼합 하는 데 사용 됩니다.

 이 문서 컨텍스트 내에 포함 된 코드 문에 대 한 범위를 가져오려면, 호출 된 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) 메서드.

## <a name="see-also"></a>참고자료
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)