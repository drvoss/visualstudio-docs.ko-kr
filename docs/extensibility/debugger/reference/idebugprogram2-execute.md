---
title: IDebugProgram2::Execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Execute
helpviewer_keywords:
- IDebugProgram2::Execute
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27730528b552e4a545725a7a7463475be6038bba
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329815"
---
# <a name="idebugprogram2execute"></a>IDebugProgram2::Execute
중지 된 상태에서이 프로그램 실행을 계속 합니다. 이전 실행 상태 (예: 단계)의 선택이 취소 되어, 프로그램이 다시 실행을 시작 하 고 있습니다.

> [!NOTE]
> 이 메서드는 사용 되지 않습니다. 사용 된 [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md) 메서드 대신 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Execute(
   void
);
```

```csharp
int Execute();
```

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 다른 프로그램의 스레드 중지 된 상태에서 실행을 시작할 때이 메서드는이 프로그램에서 호출 됩니다. 이 또한 메서드는 사용자가 선택 합니다 **시작** 명령을 합니다 **디버그** IDE의 메뉴. 이 메서드의 구현을 호출 처럼 간단할 수 있습니다 합니다 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) 프로그램의 현재 스레드에서 메서드.

> [!WARNING]
> Stopping 이벤트 또는 직접 (동기) 이벤트를 전송 하지 마십시오 [이벤트](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) 이 호출을 처리 하는 동안 그렇지 않은 경우 디버거가 중단 될 수 있습니다.

## <a name="see-also"></a>참고자료
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)