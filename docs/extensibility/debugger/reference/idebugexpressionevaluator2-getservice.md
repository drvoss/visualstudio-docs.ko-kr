---
title: IDebugExpressionEvaluator2::GetService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42a4027b4153f262eb8164a915f229f04c7cbed4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325557"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
고유 식별자를 지정 된 서비스 개체를 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetService (
   GUID        uid,
   IUnknown ** ppService
);
```

```csharp
int GetService (
   Guid       uid,
   out object ppService
);
```

## <a name="parameters"></a>매개 변수
`uid`\
[in] 검색할 서비스의 고유 식별자입니다.

`ppService`\
[out] 서비스를 나타내는 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 다른 식 계산기에서 서비스를 얻기 위한 타사 식 계산기는 에서도 사용할 수 있습니다. 예를 들어,이 메서드가 기본 식 계산기에서 시각화 도우미 서비스에 대 한 인터페이스를 가져오는 데 사용할 수 없습니다. 타사 식 계산기가이 인터페이스를 구현 해야 할 가능성이 높습니다.

## <a name="see-also"></a>참고자료
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)