---
title: IDebugReference2::GetDerivedMostReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 44413531cf3a91c6677d9ce3d56e10646307ffd6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155858"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
참조의 가장 많이 파생 참조를 가져옵니다. 나중에 사용하도록 예약되어 있습니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

#### <a name="parameters"></a>매개 변수
 `ppDerivedMost`

 [out] 반환 된 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 가장 많이 파생 속성을 나타내는 개체입니다.

## <a name="return-value"></a>반환 값
 항상 `E_NOTIMPL`를 반환합니다.

## <a name="remarks"></a>설명
 예를 들어,이 속성을 구현 하는 개체를 설명 하는 경우 `ClassRoot` 인스턴스화 실제로 이지만 `ClassDerived` 에서 파생 된 `ClassRoot`,이 메서드는 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 개체 에 대 한 참조를 나타내는 `ClassDerived` 개체입니다.

## <a name="see-also"></a>관련 항목
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)