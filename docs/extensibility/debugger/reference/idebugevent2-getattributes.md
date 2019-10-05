---
title: IDebugEvent2::GetAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3f85cccb01a31232cccc39e44fae7accbfa4f954
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327583"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
이 디버그 이벤트에 대 한 특성을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

## <a name="parameters"></a>매개 변수
`pdwAttrib`\
[out] 플래그의 조합 된 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) 열거형입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 합니다 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) 인터페이스는 모든 이벤트에 공통적으로 적용 합니다. 이 메서드가 이벤트 유형을 설명합니다. 예를 들어, 이벤트 동기 또는 비동기 이며이 stopping 이벤트.

## <a name="see-also"></a>참고자료
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)