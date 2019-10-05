---
title: 프로그램 시작 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- programs, launching
ms.assetid: 6857e9c6-e44a-468a-afa4-f7c4a0b77844
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b54250a54960f346f60c5d668755fb5d28ab376e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430201"
---
# <a name="launching-a-program"></a>프로그램 시작
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로그램을 디버깅 하려는 사용자가 IDE에서 디버거를 실행 하도록 f5 수 있습니다. 이 일련의 궁극적으로 IDE의 다시 연결 되거나 연결 프로그램에 다음과 같이 되는 디버그 엔진 (DE)에 연결 하는 이벤트를 시작 합니다.  
  
1. IDE는 먼저 현재 프로젝트는 솔루션의 디버그 설정을 가져올 프로젝트 패키지를 호출 합니다. 시작 디렉터리, 환경 변수, 프로그램 실행은 포트 및 지정 된 경우 해당 프로그램을 만드는 데 DE의 설정에 포함 됩니다. 이러한 설정은 디버그 패키지에 전달 됩니다.  
  
2. DE 지정 된 경우는 DE 프로그램을 시작 하려면 운영 체제를 호출 합니다. 프로그램 시작에 따라 프로그램의 런타임 환경이 로드 됩니다. 예를 들어 프로그램 MSIL로 작성 하는 경우 프로그램을 실행 하려면 공용 언어 런타임에서 호출 됩니다.  
  
    또는  
  
    DE 지정 하지 않으면 포트 로드할 프로그램의 런타임 환경을 사용 하면 되는 프로그램을 시작 하려면 운영 체제를 호출 합니다.  
  
   > [!NOTE]
   > 프로그램을 실행 하는 DE가 사용 하는 경우 가능성이 동일한 DE는 프로그램에 연결 됩니다.  
  
3. 여부는 DE 포트나 시작 프로그램에 따라는 DE 또는 런타임 환경에서 다음 프로그램 설명 또는 노드를 만들고 프로그램이 실행 되는 포트를에 알립니다.  
  
   > [!NOTE]
   > 프로그램 노드는 디버깅할 수 있는 프로그램의 간단한 표현 하기 때문에 런타임 환경을 프로그램 노드를 만든 것이 좋습니다. 방금를 만들고 프로그램 노드를 등록 하는 전체 DE를 로드 하지 않아도가 됩니다. DE은 실제로 실행 되는 IDE만 없습니다 IDE 중 실행 경우 포트로 프로그램 노드를 추가할 수 있는 구성 요소 필요 합니다.  
  
   다른 프로그램을 함께 새로 만든된 프로그램 관련 관련 되지 않은, 시작 또는 동일한 IDE에서 디버그 세션 구성에 연결 합니다.  
  
   프로그래밍 방식으로 처음 누를 때 **F5**를 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]의 (연결 된 형식으로 시작 하는 프로그램) 프로젝트 패키지를 호출 하는 디버그 패키지를 통해를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> 메서드를 다시 채웁니다를 <xref:Microsoft.VisualStudio.Shell.Interop.VsDebugTargetInfo2> 솔루션의 활성 프로젝트 디버그 설정 사용 하 여 구조입니다. 이 구조는 호출을 통해 디버그 패키지에 다시 전달 되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebugger2.LaunchDebugTargets2%2A> 메서드. 그런 다음 디버그 패키지 디버깅 및 모든 관련 된 디버그 엔진 되 고 프로그램을 시작 하는 세션 디버그 관리자를 (SDM)를 인스턴스화합니다.  
  
   SDM 전달 되는 인수 중 하나는 프로그램을 시작 하는 데는 DE의 GUID입니다.  
  
   DE GUID 없으면 `GUID_NULL`, SDM 공동 DE, 만들고 호출 해당 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) 프로그램을 시작 하는 방법입니다. 예를 들어 프로그램이 네이티브 코드에서 작성 되는 경우 `IDebugEngineLaunch2::LaunchSuspended` 아마도 호출 `CreateProcess` 및 `ResumeThread` (Win32 함수) 프로그램을 실행 합니다.  
  
   프로그램 시작에 따라 프로그램의 런타임 환경이 로드 됩니다. DE 또는 런타임 환경을 만듭니다는 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) 프로그램에 설명 하는 인터페이스 및이 인터페이스를 전달 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) 프로그램이 포트에 알리기 위해 실행 중입니다.  
  
   경우 `GUID_NULL` 프로그램을 시작 하는 포트를 전달 됩니다. 프로그램이 실행 되 면 런타임 환경을 만듭니다는 `IDebugProgramNode2` 프로그램에 설명 하는 인터페이스 및 전달 `IDebugPortNotify2::AddProgramNode`합니다. 이 프로그램이 실행 되는 포트를 알립니다. 다음은 SDM 실행 중인 프로그램 디버그 엔진에 연결합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [포트에 알림](../../extensibility/debugger/notifying-the-port.md)  
 프로그램이 시작 되 고 포트를 알려 줍니다 후의 상황에 대해 설명 합니다.  
  
 [시작 후 연결](../../extensibility/debugger/attaching-after-a-launch.md)  
 디버그 세션을 DE 프로그램에 연결할 준비가 되 면 문서입니다.  
  
## <a name="related-sections"></a>관련 단원  
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)  
 프로그램을 시작 하 고 식을 계산 하는 등의 다양 한 디버깅 작업에 대 한 링크를 포함 합니다.
