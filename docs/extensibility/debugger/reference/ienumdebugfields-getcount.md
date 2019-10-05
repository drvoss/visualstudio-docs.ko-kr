---
title: IEnumDebugFields::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFields::GetCount
helpviewer_keywords:
- IEnumDebugFields::GetCount method
ms.assetid: 3f471b40-4db3-49f7-b504-58b2476eef74
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bb0c28f72b88822d87af928b9e0ce689cf0f3a7d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350460"
---
# <a name="ienumdebugfieldsgetcount"></a>IEnumDebugFields::GetCount
이 메서드는 열거형의 요소 수를 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>매개 변수
`pcelt`\
[out] 열거형의 요소 수를 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 다음, 복제, Skip 및 재설정 구현 해야를 지정 하는 일반적인 COM 열거형 인터페이스의 일부가 아닙니다.

## <a name="see-also"></a>참고자료
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)