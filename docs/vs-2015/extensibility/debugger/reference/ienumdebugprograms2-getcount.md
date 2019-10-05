---
title: IEnumDebugPrograms2::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::GetCount
helpviewer_keywords:
- IEnumDebugPrograms2::GetCount
ms.assetid: 84832982-fa68-4090-a5b7-b233817876b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1a3f9dd89969e7457fe6838d2a3529d89d8ce72
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199607"
---
# <a name="ienumdebugprograms2getcount"></a>IEnumDebugPrograms2::GetCount
열거형의 요소 수를 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCount(
   ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

#### <a name="parameters"></a>매개 변수
 `pcelt`

 [out] 열거형의 요소 수를 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 항목만 지정 하는 일반적인 COM 열거형 인터페이스의 일부가 아닙니다.는 `Next`, `Clone`를 `Skip`, 및 `Reset` 메서드를 구현 해야 합니다.

## <a name="see-also"></a>참고 항목
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)