---
title: 솔루션의 프로젝트 로드 관리 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solutions, managing project loading
ms.assetid: 097c89d0-f76a-4aaf-ada9-9a778bd179a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a80430c4a5dcf5526445275b89fa2da7f02f5529
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340593"
---
# <a name="manage-project-loading-in-a-solution"></a>솔루션의 프로젝트 로드 관리
Visual Studio 솔루션을 다 수의 프로젝트를 포함할 수 있습니다. 기본 Visual Studio 동작은 솔루션을 열 때 솔루션의 모든 프로젝트를 로드 하 고 사용자가 프로젝트 모두 로드 작업이 완료 될 때까지 액세스할 수 없도록 합니다. 프로젝트 로드 하는 과정은 2 분 이상 지속 로드 되는 프로젝트의 수와 프로젝트의 총 수를 보여 주는 진행률 표시줄이 표시 됩니다. 사용자는 여러 프로젝트가 포함 된 솔루션에서 작업 하는 동안 프로젝트를 언로드할 수 있지만이 절차에 몇 가지 단점이 있습니다: 언로드된 프로젝트에는 솔루션 다시 빌드 명령의 일부로 빌드되지 않는 닫은 IntelliSense 설명은 형식 및 멤버 프로젝트 표시 되지 않습니다.

 개발자는 솔루션 로드 시간을 줄이고 하 고 관리자 솔루션 로드를 만들어 동작을 로드 하는 프로젝트를 관리할 수 있습니다. 솔루션 로드 관리자 프로젝트는 백그라운드 빌드를 시작 하기 전에 로드 되었는지 확인 하 고 다른 백그라운드 작업이 완료 될 때까지 백그라운드 로드를 지연 하 고 다른 프로젝트 로드 관리 작업을 수행할 수 있습니다.

## <a name="create-a-solution-load-manager"></a>솔루션 로드 관리자를 만듭니다.
 개발자 만들면 솔루션 로드 관리자를 구현 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager> 알릴 Visual Studio 솔루션 로드 관리자 활성 상태 인지 확인 합니다.

### <a name="activate-a-solution-load-manager"></a>솔루션 로드 관리자 활성화
 Visual Studio에서는 하나의 솔루션 로드 관리자 지정된 된 시간에 하므로 알려 Visual Studio 솔루션 부하를 활성화 하려는 경우 관리자입니다. 두 번째 솔루션 로드 관리자는 나중에 활성화 되 면 관리자에 게 솔루션 부하의 연결이 끊어집니다.

 가져와야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution> 서비스와 설정의 [__VSPROPID4 합니다. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) 속성:

```csharp
IVsSolution pSolution = GetService(typeof(SVsSolution)) as IVsSolution;
object objLoadMgr = this;   //the class that implements IVsSolutionManager
pSolution.SetProperty((int)__VSPROPID4.VSPROPID_ActiveSolutionLoadManager, objLoadMgr);
```

 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadManager.OnDisconnect%2A> Visual Studio를 종료 하는 경우 또는 다른 패키지를 호출 하 여 활성 솔루션 로드 관리자로 동안 수행 된 경우 메서드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.SetProperty%2A> 사용 하 여는 [__VSPROPID4 합니다. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) 속성입니다.

#### <a name="strategies-for-different-kinds-of-solution-load-manager"></a>다양 한 종류의 솔루션 로드 관리자에 대 한 전략
 솔루션 로드 관리자 관리 하는 솔루션 유형에 따라 다른 방법으로 구현할 수 있습니다.

 솔루션 로드 관리자 일반적으로 로드 하는 솔루션을 관리 되어야 하는 경우에 VSPackage의 일부로 구현할 수 있습니다. 추가 하 여 패키지를 자동 로드로 설정 해야 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> 값을 사용 하 여 VSPackage에 <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionOpening_guid>입니다. 솔루션 로드 관리자에서 활성화할 수 있습니다는 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드.

> [!NOTE]
> 자동 로드 패키지에 대 한 자세한 내용은 참조 하세요. [Vspackage 로드](../extensibility/loading-vspackages.md)합니다.

 Visual Studio에서 마지막 솔루션 로드 관리자만 활성화할를 인식 하므로 일반 솔루션 로드 관리자 자체를 활성화 하기 전에 기존 부하 관리자 인지 여부를 탐지 항상 해야 합니다. 호출 하는 경우 `GetProperty()` 에 대 한 솔루션 서비스 [__VSPROPID4 합니다. VSPROPID_ActiveSolutionLoadManager](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_ActiveSolutionLoadManager>) 반환 `null`, 관리자가 없거나 활성 솔루션 로드 합니다. Null 반환 하지 않으면, 솔루션 로드 관리자로 서 개체가 같은지 여부를 확인 합니다.

 VSPackage 솔루션 로드 이벤트를 구독할 수 솔루션 로드 관리자 관리 솔루션의 몇 가지 형식만 되어야 하는 경우 (호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A>), 이벤트 처리기를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A> 솔루션 로드 관리자를 활성화 하려면.

 활성화 정보를 호출 하 여 솔루션 파일의 일부로 지속할 수 솔루션 로드 관리자만 특정 솔루션을 관리 하려는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A> 사전 해결 방법 섹션에 대 한 합니다.

 특정 솔루션 로드 관리자에서 자체를 비활성화 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents.OnAfterCloseSolution%2A> 다른 솔루션 로드 관리자를 사용 하 여 충돌 하는 순서 대로 이벤트 처리기입니다.

 전역 프로젝트 로드 속성 (예를 들어에 설정 된 속성 옵션 페이지)를 유지 하기 위해 솔루션 로드 관리자에서 활성화할 수 있습니다만 솔루션 로드 관리자는 경우는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 이벤트 처리기 다음 솔루션 속성에서 설정 유지 솔루션 로드 관리자를 비활성화 합니다.

## <a name="handle-solution-load-events"></a>솔루션 로드 이벤트를 처리 합니다.
 솔루션 로드 이벤트를 구독 하려면 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AdviseSolutionEvents%2A> 관리자에 게 솔루션 로드를 활성화할 때입니다. 구현 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents>, 속성을 로드 하는 다른 프로젝트와 관련 된 이벤트에 응답할 수 있습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeOpenSolution%2A>: 솔루션을 열기 전에이 이벤트가 발생 합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeBackgroundSolutionLoadBegins%2A>: 솔루션이 완전히 로드 되었지만 백그라운드 하기 전에 프로젝트를 로드 다시 시작 후이 이벤트가 발생 합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterBackgroundSolutionLoadComplete%2A>: 이 이벤트는 솔루션 로드 관리자가 있는지 여부 솔루션을 처음에 완전히 로드 되 면 발생 합니다. 솔루션이 완전히 로드 될 때마다 백그라운드 로드 나 요청 시 로드 후에 실행 됩니다. 동시에, <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExistsAndFullyLoaded_guid> 다시 활성화 됩니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnQueryBackgroundLoadProjectBatch%2A>: 이 이벤트는 프로젝트 (또는 프로젝트)의 로드 하기 전에 발생 합니다. 다른 백그라운드 프로세스가 완료 된 후에 프로젝트가 로드 되도록 설정 `pfShouldDelayLoadToNextIdle` 하 **true**합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnBeforeLoadProjectBatch%2A>: 이 이벤트는 프로젝트의 일괄 처리 로드 되려고 할 때 발생 합니다. 하는 경우 `fIsBackgroundIdleBatch` 가 true 이면; 백그라운드에서 로드할 경우 프로젝트에는 `fIsBackgroundIdleBatch` 이 false 인 경우 프로젝트는 로드할 사용자 요청을 동기적으로 인해 예를 들어 사용자 경우 솔루션 탐색기에서 보류 중인 프로젝트를 확장 합니다. 그렇지 않은 경우 수행 해야 하는 비용이 많이 드는 작업을 수행 하려면이 이벤트를 처리할 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A>합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionLoadEvents.OnAfterLoadProjectBatch%2A>: 이 이벤트는 프로젝트의 일괄 처리 로드 되 면 발생 합니다.

## <a name="detect-and-manage-solution-and-project-loading"></a>검색 및 관리 솔루션 및 프로젝트 로드
 프로젝트 및 솔루션 로드 상태를 검색 하기 위해 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProperty%2A> 다음 값을 사용 하 여:

- [__VSPROPID4 합니다. VSPROPID_IsSolutionFullyLoaded](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsSolutionFullyLoaded>): `var` 반환 `true` 솔루션과 해당 프로젝트가 모두 로드 되 면, 그렇지 않으면 `false`합니다.

- [__VSPROPID4 합니다. VSPROPID_IsInBackgroundIdleLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInBackgroundIdleLoadProjectBatch>): `var` 반환 `true` 하는 경우 프로젝트의 일괄 처리 현재 로드 되는 백그라운드에서이 고, 그렇지 `false`합니다.

- [__VSPROPID4 합니다. VSPROPID_IsInSyncDemandLoadProjectBatch](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID4.VSPROPID_IsInSyncDemandLoadProjectBatch>): `var` 반환 `true` 경우 프로젝트의 일괄 처리는 현재으로 로드 되는 사용자 명령 또는 기타 명시적 로드의 결과로 고, 그렇지 `false`합니다.

- [__VSPROPID2 합니다. VSPROPID_IsSolutionClosing](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID2.VSPROPID_IsSolutionClosing>): `var` 반환 `true` 닫혀 있는 경우 솔루션 현재 되 고 그렇지 않으면 `false`합니다.

- [__VSPROPID 합니다. VSPROPID_IsSolutionOpening](<xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID.VSPROPID_IsSolutionOpening>): `var` 반환 `true` 솔루션을 현재을 여는 그렇지 않은 경우 `false`합니다.

또한 다음 방법 중 하나를 호출 하 여 프로젝트 및 솔루션 로드 되었음을 확인할 수 있습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureSolutionIsLoaded%2A>: 메서드가 반환 되기 전에 로드 하기 위해 솔루션의 프로젝트를 강제로이 메서드를 호출 합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectIsLoaded%2A>: 프로젝트를 강제로이 메서드를 호출 `guidProject` 메서드가 반환 되기 전에 로드 합니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution4.EnsureProjectsAreLoaded%2A>:에서 프로젝트를 강제로이 메서드를 호출 `guidProjectID` 메서드가 반환 되기 전에 로드 합니다.
