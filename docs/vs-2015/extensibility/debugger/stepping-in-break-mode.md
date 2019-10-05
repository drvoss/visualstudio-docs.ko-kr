---
title: 중단 모드 단계별 실행 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 482d7131692c1e22483c80f4b4bb22e07a6caf1a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423363"
---
# <a name="stepping-in-break-mode"></a>중단 모드 단계별 실행
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

다음은 디버거가 중단 모드 이며 코드를 단계별로 실행 해야 하는 경우 발생 하는 프로세스에 대 한 설명입니다.  
  
## <a name="stepping-process"></a>단계별 프로세스  
  
1. 호출 [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md) 사용 하 여 [STEPKIND](../../extensibility/debugger/reference/stepkind.md) 하 고 [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) 단계의 실행에 대 한 인수입니다.  
  
2. 단계가 완료 되 면 송신을 [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) 중지 이벤트입니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 이벤트 호출](../../extensibility/debugger/calling-debugger-events.md)
