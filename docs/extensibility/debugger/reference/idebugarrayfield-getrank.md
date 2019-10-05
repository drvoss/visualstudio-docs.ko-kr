---
title: IDebugArrayField::GetRank | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33d5118ffa045ccc2315ccb596850be6922fc2ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321683"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
순위 또는 배열의 차원 수를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>매개 변수
`pdwRank`\
[out] 순위를 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 합니다. 그렇지 않으면 오류 코드를 반환합니다.

## <a name="remarks"></a>설명
 배열 차수 차원 수에 해당합니다. C++ 및 C#에서 다차원 배열의 배열은 실제로 배열과 따라서는 1 차원 배열에만 간주 될 수 있습니다 (및 `GetRank` 메서드는 항상 1을 반환). [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], 반면에 다차원 배열 다르게 처리 됩니다 및 차원 수를 반영 하는 이러한 배열 차수 (및 `GetRank` 메서드는 항상 차원 수가 반환).

## <a name="see-also"></a>참고자료
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)