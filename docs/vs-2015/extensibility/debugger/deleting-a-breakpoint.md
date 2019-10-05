---
title: 중단점 삭제 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42cd353c216c21d14c4f6592da809c72acdba664
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63409402"
---
# <a name="deleting-a-breakpoint"></a>중단점 삭제
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음은 보류 중인 중단점을 삭제 하는 경우 프로세스.  
  
## <a name="deletion-process"></a>삭제 프로세스  
 세션 디버그 관리자 (SDM) 호출을 [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) 보류 중인 중단점 및 바인딩된 모든 중단점을 제거 하는 방법에서 바인딩됩니다.  
  
> [!NOTE]
> 호출 하 여 단일 바인딩된 중단점을 삭제할 수도 있습니다 [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
