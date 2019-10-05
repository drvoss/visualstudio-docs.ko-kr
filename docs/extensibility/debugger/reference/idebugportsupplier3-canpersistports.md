---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 11bc6e21e8b70a5bd95c001f4173a7da3f3fe4be
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340065"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
이 메서드는 지속할 지 여부를 포트 공급자 수 포트 (디스크에 쓴 후)에서 디버거는 호출 간에 결정 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>매개 변수
 없음

## <a name="return-value"></a>반환 값
 `S_OK` 포트를 유지 하는 경우 또는 `S_FALSE` 나타내는 포트를 유지할 수 없습니다.

## <a name="remarks"></a>설명
 포트 공급자는 포트를 유지할 수 있습니다, 소멸 될 때 사용자에 게 이렇게 하며 다음 다시 한 번 인스턴스화될 때 다시 로드 합니다.

## <a name="see-also"></a>참고자료
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)