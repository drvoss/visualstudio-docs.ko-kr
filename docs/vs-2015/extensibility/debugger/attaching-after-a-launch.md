---
title: 시작 후 연결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437430"
---
# <a name="attaching-after-a-launch"></a>시작 후 연결
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로그램 시작 디버그 세션 언급된 프로그램에 디버그 엔진 (DE)를 연결할 준비가 된 것입니다.  
  
## <a name="design-decisions"></a>디자인 결정  
 통신 공유 되는 주소 공간 내에서 쉽게 이기 때문에 디버그 세션 사이 DE, 또는 DE와 프로그램 간의 통신을 용이 하 게 더 적합 한지 결정 해야 합니다. 다음 중에서 선택 합니다.  
  
- 디버그 세션을 DE 사이의 의사 소통을 촉진 하는 것에 있도록 하는 경우 다음 디버그 세션 공동는 DE 만들고 프로그램에 연결 하는 DE 요청 합니다. 이런 디버그 세션 및 DE 함께 주소 공간 및 런타임 환경과 프로그램에서 다른 함께 있습니다.  
  
- 하는 경우는 DE와 프로그램 간의 의사 소통을 촉진 하는 것, 그런 다음 런타임 환경 공동 만듭니다는 DE. 이런 주소 공간에서 SDM DE, 런타임 환경 및 프로그램 다른 함께 있습니다. 스크립트 언어를 실행 하려면 인터프리터를 사용 하 여 구현 되는 DE 일반적입니다.  
  
    > [!NOTE]
    > DE 프로그램에 연결 하는 방법을 하는 것은 구현에 따라 다릅니다. DE와 프로그램 간의 통신 구현에 따라 다릅니다 이기도합니다.  
  
## <a name="implementation"></a>구현  
 프로그래밍 방식으로 세션 디버그 관리자 SDM ()를 처음 받을 때 합니다 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) 호출을 실행 하도록 프로그램을 나타내는 개체를 [연결](../../extensibility/debugger/reference/idebugprogram2-attach.md) 메서드를 전달는 [ IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) SDM 돌아가기 디버그 이벤트를 전달 하는 데 개체 이상입니다. 합니다 `IDebugProgram2::Attach` 메서드를 호출 합니다 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) 메서드. SDM 받는 방법에 대 한 자세한 내용은 합니다 `IDebugProgram2` 인터페이스를 참조 하십시오 [포트에 알림](../../extensibility/debugger/notifying-the-port.md)합니다.  
  
 프로그램 DE 디버깅 중인 프로그램에 일반적으로 DE 스크립트를 실행 하는 인터프리터의 일부 이므로와 동일한 주소 공간에서 실행 해야 하는 경우는 `IDebugProgramNodeAttach2::OnAttach` 메서드가 반환 되는 `S_FALSE`, 연결 프로세스 완료를 나타내는입니다.  
  
 DE은 SDM의 주소 공간에서 실행 되는 반면, 하는 경우는 `IDebugProgramNodeAttach2::OnAttach` 메서드가 반환 `S_OK` 또는 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) 인터페이스에 전혀 구현 되지 않습니다는 [IDebugProgramNode2 ](../../extensibility/debugger/reference/idebugprogramnode2.md) 디버그 중인 프로그램과 관련 된 개체입니다. 이 경우에 [연결](../../extensibility/debugger/reference/idebugengine2-attach.md) 결국 메서드는 연결 작업이 완료 합니다.  
  
 후자의 경우에 호출 해야 합니다는 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) 메서드를 `IDebugProgram2` 에 전달 된 개체를 `IDebugEngine2::Attach` 메서드, 저장소를 `GUID` 로컬 프로그램에서 개체 및이 반환 `GUID` 때를 `IDebugProgram2::GetProgramId` 이 개체에서 메서드 호출 이후에 됩니다. `GUID` 다양 한 디버그 구성에서 프로그램을 고유 하 게 식별 하는 데 사용 됩니다.  
  
 경우에를 `IDebugProgramNodeAttach2::OnAttach` 메서드 반환 `S_FALSE`의 `GUID` 를 해당 메서드에 전달 되는 프로그램에 사용할 이므로 `IDebugProgramNodeAttach2::OnAttach` 설정 하는 메서드를 `GUID` 로컬 program 개체에서.  
  
 프로그램 및 시작 이벤트를 보낼 준비가 이제는 DE 연결 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로그램에 직접 연결](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [포트에 알림](../../extensibility/debugger/notifying-the-port.md)   
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md)
