---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec541b6dc4ccae57628d4b33e7c188008da6edae
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187956"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
이 메서드는 사용자는 안전 하지 않은 프로세스에 연결 하려면 먼저 경고를 표시 하려면 포트 공급자를 사용 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT QueryCanSafelyAttach();
```

```csharp
int QueryCanSafelyAttach();
```

## <a name="return-value"></a>반환 값
 반환 값은 아래와 같습니다.

- `S_OK`: 프로세스에 연결 하는 것이 안전 하 고 경고 대화 상자가 표시 됩니다.

- `S_FALSE`: 연결 보안 문제가 될 수 하 고 경고 대화 상자가 표시 됩니다.

- `FAILURE`: 프로세스에 연결 실패 합니다.

## <a name="see-also"></a>관련 항목
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)