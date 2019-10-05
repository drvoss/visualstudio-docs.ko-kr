---
title: IEnumDebugPrograms2::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Clone
helpviewer_keywords:
- IEnumDebugPrograms2::Clone
ms.assetid: 880846c2-39d3-45cd-85c3-ad5409a3710f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7fd4f8719fdd5f587d1ac5305245f87ff1fd65d2
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317123"
---
# <a name="ienumdebugprograms2clone"></a>IEnumDebugPrograms2::Clone
별도 개체와 현재 열거형의 복사본을 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Clone(
   IEnumDebugPrograms2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPrograms2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
[out] 이 열거형은 개별 개체로 복사본을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 열거형의 복사본을이 메서드는 시간에 원본과 동일한 상태를 있습니다. 그러나 복사본의 및는 원래 상태는 각각 별도 이며 개별적으로 변경할 수 있습니다.

## <a name="see-also"></a>참고자료
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)