---
title: 세션 디버그 관리자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9fd7c7555c19f850a15161f6fba00b1184621a9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157832"
---
# <a name="session-debug-manager"></a>세션 디버그 관리자
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

세션 디버그 관리자 SDM ()는 임의 개수의 임의 개수의 임의 개수의 컴퓨터에서 여러 프로세스에서 프로그램을 디버깅 디버그 엔진 (DE)를 관리 합니다. 멀티플렉서 디버그 엔진 뿐만 SDM IDE에 디버그 세션의 통합된 보기를 제공 합니다.  
  
## <a name="session-debug-manager-operation"></a>세션 디버그 관리자 작업  
 세션 디버그 관리자 SDM ()는 DE를 관리합니다. 컴퓨터에서 동시에 실행 하는 둘 이상의 디버그 엔진 있을 수 있습니다. DEs을 다중 송신할 수 SDM는 다양 한 인터페이스는 DEs에서 래핑하고 단일 인터페이스로 IDE에 노출 합니다.  
  
 성능을 향상 시키려면 일부 인터페이스 하지 멀티플렉싱 됩니다. 대신, DE에서 직접 사용 하는 하 고 이러한 인터페이스에 대 한 호출에서 SDM 통과 하지 않습니다. 예를 들어, 특정 명령, 메모리 또는 특정 독일에서 디버깅 하는 특정 프로그램의 문서를 참조 하므로 메모리, 코드 및 문서 컨텍스트를 사용 하는 인터페이스는 멀티플렉싱 하지 않습니다. 없는 다른 DE 통신의 해당 수준에 참여 해야 합니다.  
  
 모든 컨텍스트는 그렇지 않습니다. 식 평가 컨텍스트 인터페이스에 대 한 호출 SDM을 통해 이동합니다. 식 평가 중 SDM 래핑하는 [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) 해당 식을 계산할 때 디버깅 프로그램 될 수 있는 동일한 프로세스에서 사용 되는 여러 DEs 포함 될 수 있으므로 IDE를 제공 하는 인터페이스 동일한 스레드에서 실행 됩니다.  
  
 SDM 위임 메커니즘으로 일반적으로 작동 하지만 브로드캐스트 메커니즘으로 작용할 수 있습니다. 예를 들어, 식 평가 중 SDM 코드 지정한 스레드에서 실행할 수 있는지 모든 DEs 알림 브로드캐스트 메커니즘으로 작동 합니다. 마찬가지로, SDM stopping 이벤트를 받으면 실행 중지 해야 하는 모든 프로그램을 브로드캐스트합니다. 단계를 호출 하면 SDM 브로드캐스트합니다 하 고 모든 프로그램 실행을 계속 수 있습니다. 중단점은 또한 모든 DE에 브로드캐스트 됩니다.  
  
 현재 프로세스, 스레드 또는 스택 프레임은 SDM 추적 하지 않습니다. 프로세스, 프로그램 및 스레드 정보는 특정 디버깅 이벤트와 함께에서 SDM로 전송 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버그 엔진](../../extensibility/debugger/debug-engine.md)   
 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)   
 [디버거 컨텍스트](../../extensibility/debugger/debugger-contexts.md)
