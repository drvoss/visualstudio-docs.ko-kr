---
title: 중단점 삭제 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7551ee12993780544bbb9c9eb127a9bfb4364e8d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345824"
---
# <a name="deleting-a-breakpoint"></a>중단점 삭제
다음은 보류 중인 중단점을 삭제 하는 경우 프로세스.

## <a name="deletion-process"></a>삭제 프로세스
 세션 디버그 관리자 (SDM) 호출을 [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) 보류 중인 중단점 및 바인딩된 모든 중단점을 제거 하는 방법에서 바인딩됩니다.

> [!NOTE]
> 호출 하 여 단일 바인딩된 중단점을 삭제할 수도 있습니다 [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)합니다.

## <a name="see-also"></a>참고자료
- [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)