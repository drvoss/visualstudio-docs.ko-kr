---
title: 중단점 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- breakpoints, deleting
- debugging [Debugging SDK], deleting breakpoints
ms.assetid: 75a046cc-d20a-4c79-ad2d-1f18426ac5d0
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b53be5e09d4579d95cb4b9d9726d6087effb8ff1
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797392"
---
# <a name="deleting-a-breakpoint"></a>중단점 삭제
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음은 보류 중인 중단점을 삭제 하는 경우 프로세스.  
  
## <a name="deletion-process"></a>삭제 프로세스  
 세션 디버그 관리자 (SDM) 호출을 [IDebugPendingBreakpoint2::Delete](../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md) 보류 중인 중단점 및 바인딩된 모든 중단점을 제거 하는 방법에서 바인딩됩니다.  
  
> [!NOTE]
>  호출 하 여 단일 바인딩된 중단점을 삭제할 수도 있습니다 [IDebugBoundBreakpoint2::Delete](../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)

