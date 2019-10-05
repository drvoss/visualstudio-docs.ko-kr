---
title: IDebugProgramNodeAttach2::OnAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNodeAttach2::OnAttach
helpviewer_keywords:
- IDebugProgramNodeAttach2::OnAttach
ms.assetid: 5fe52761-a508-4ab5-abdb-334fb6590334
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 01958b26b5b381bdbe51c2648d2751e822002e6b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325050"
---
# <a name="idebugprogramnodeattach2onattach"></a>IDebugProgramNodeAttach2::OnAttach
연결된 프로그램에 연결 하거나 연결 프로세스를 지연 합니다 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드.

## <a name="syntax"></a>구문

```cpp
HRESULT OnAttach(
   [in] REFGUID guidProgramId
);
```

```csharp
int OnAttach(
   ref Guid guidProgramId
};
```

## <a name="parameters"></a>매개 변수
`guidProgramId`\
[in] `GUID` 연결된 프로그램에 할당 합니다.

## <a name="return-value"></a>반환 값
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 경우는 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드를 호출 해야 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 이 메서드는 연결 프로세스 중 전에 합니다 [연결](../../../extensibility/debugger/reference/idebugengine2-attach.md) 메서드가 호출 됩니다. `OnAttach` 메서드 자체 연결 프로세스를 수행할 수 있습니다 (이 메서드가 반환 하는 경우에 `S_FALSE`) 연결 프로세스를 지연 또는 `IDebugEngine2::Attach` 메서드 (합니다 `OnAttach` 메서드가 반환 되는 `S_OK`). 하거나 이벤트에 `OnAttach` 메서드를 설정할 수는 `GUID` 하려면 디버깅 중인 프로그램의는 지정 `GUID`합니다.

## <a name="see-also"></a>참고자료
- [IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)