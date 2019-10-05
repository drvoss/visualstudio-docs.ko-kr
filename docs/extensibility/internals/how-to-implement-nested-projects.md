---
title: '방법: 중첩 된 프로젝트를 구현 합니다. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7219824bf7cc13f8fe00ebc9be0320e557f0fcf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328681"
---
# <a name="how-to-implement-nested-projects"></a>방법: 중첩 된 프로젝트를 구현 합니다.

중첩 된 프로젝트 유형을 만들면 구현 해야 하는 몇 가지 추가 단계가 있습니다. 부모 프로젝트를 솔루션의 중첩 된 (자식) 프로젝트에 동일한 작업을 수행 중 일부에 적용 됩니다. 부모 프로젝트는 유사한 솔루션에 프로젝트의 컨테이너입니다. 특히, 중첩 된 프로젝트의 계층 구조를 빌드할 부모 프로젝트 및 솔루션에서 발생 해야 하는 여러 이벤트 있습니다. 이러한 이벤트는 중첩 된 프로젝트를 만들기 위한 다음 프로세스에 설명 되어 있습니다.

## <a name="create-nested-projects"></a>중첩 된 프로젝트 만들기

1. 호출 하 여 부모 프로젝트의 프로젝트 파일 및 시작 정보를 로드 하는 통합된 개발 환경 (IDE)는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 인터페이스입니다. 부모 프로젝트 생성 되어 솔루션에 추가 합니다.

    > [!NOTE]
    > 이 시점에서 것 하위 프로젝트를 만들기 전에 부모 프로젝트를 만들어야 하기 때문에 중첩 된 프로젝트를 만들 부모 프로젝트의 프로세스에서 너무 이릅니다. 이 시퀀스 다음 상위 프로젝트 하위 프로젝트에 설정을 적용할 수 있습니다 및 필요한 경우 하위 프로젝트에서 부모 프로젝트에서 정보를 얻을 수 있습니다. 이 순서는 필요한 경우에 소스 코드 제어 (SCC)와 같은 클라이언트가 및 **솔루션 탐색기**합니다.

     부모 프로젝트까지 기다려야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> 프로젝트 또는 프로젝트에 중첩 된 (자식)을 만들 수는 IDE에서 호출 될 메서드입니다.

2. IDE 호출 `QueryInterface` 에 대 한 부모 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>합니다. 하는 경우이 호출이 성공 하면 IDE 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> 부모 프로젝트에 대 한 중첩 된 프로젝트의 모든 열을 부모 메서드.

3. 부모 프로젝트 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> 프로젝트를 중첩 하는 수신기에 알리기 위해 메서드를 만들 수 있습니다. 예를 들어, 소스 코드 제어, 솔루션 및 프로젝트 만들기 프로세스의 단계를 순서 대로 발생 하는 경우 알아야 해당 이벤트를 수신 됩니다. 단계 순서가 발생 하는 경우 솔루션 등록 되지 소스 코드 제어를 사용 하 여 올바르게 합니다.

4. 부모 프로젝트 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> 메서드 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> 메서드를 각 자식 프로젝트에 해당 합니다.

     전달 <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> 에 `AddVirtualProject` 가상 (중첩 된) 프로젝트의 빌드에서 제외 되는 프로젝트 창에 추가 해야 함을 표시 하는 방법 등에 소스 코드 제어에 추가 합니다. `VSADDVPFLAGS` 중첩 된 프로젝트의 표시 유형을 제어 하 고 연결 된 기능 임을 수 있습니다.

     프로젝트 GUID 부모 프로젝트의 프로젝트 파일을 호출 하 여 부모 프로젝트에 저장 된 기존 자식 프로젝트 다시 로드 하는 경우 `AddVirtualProjectEx`합니다. 간의 유일한 차이점 `AddVirtualProject` 하 고 `AddVirtualProjectEX` 는 `AddVirtualProjectEX` 지정 하는 부모 프로젝트를 사용 하도록 설정 하는 매개 변수가 인스턴스당 `guidProjectID` 수 있도록 자식 프로젝트에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> 함수 올바르게 합니다.

     GUID 사용 가능한 경우,이 솔루션은 시간에 프로젝트에 대해 하나 생성 새 중첩된 프로젝트에 추가 하면 같은 부모에 추가 됩니다. 해당 프로젝트는 프로젝트 파일의 GUID를 유지 하기 위해 부모 프로젝트의 담당 합니다. 중첩 된 프로젝트를 삭제 하면 해당 프로젝트에 대 한 GUID도 삭제할 수 있습니다.

5. IDE 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> 부모 프로젝트의 각 자식 프로젝트에는 메서드.

     부모 프로젝트를 구현 해야 `IVsParentProject` 프로젝트 중첩 하려는 경우. 하지만 부모 프로젝트 호출 되지 않습니다 `QueryInterface` 에 대 한 `IVsParentProject` 부모 프로젝트 아래에 있는 경우에 합니다. 솔루션에 대 한 호출을 처리 `IVsParentProject` 호출을 구현 하는 경우 및 `OpenChildren` 중첩 된 프로젝트를 만듭니다. `AddVirtualProjectEX` 항상 라고 `OpenChildren`합니다. 되지 순서로 생성 이벤트 계층 구조를 유지 하려면 부모 프로젝트에서 호출 해야 합니다.

6. IDE 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> 자식 프로젝트는 메서드.

7. 부모 프로젝트 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> 메서드를 부모 자식 프로젝트가 만들어졌는지 수신기에 알립니다.

8. 호출 하 여 IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> 모든 자식 프로젝트가 열린 후 부모 프로젝트 메서드.

     부모 프로젝트를 호출 하 여 중첩 된 각 프로젝트에 대 한 GUID를 만들고 아직 존재 하지 않는 경우 `CoCreateGuid`합니다.

    > [!NOTE]
    > `CoCreateGuid` GUID를 만들려는 경우에 COM API 호출 됩니다. 자세한 내용은 참조 하세요. `CoCreateGuid` 및 MSDN 라이브러리의 Guid입니다.

     부모 프로젝트 다음에 IDE에서 열릴 때 검색할 프로젝트 파일에이 GUID를 저장 합니다. 호출을 관련 된 자세한 내용은 4 단계를 참조 하세요 `AddVirtualProjectEX` 검색할는 `guidProjectID` 자식 프로젝트에 대 한 합니다.

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 다음 메서드는 부모 ItemID에 대 한 규칙에 따라 위임 하에서 중첩된 프로젝트에. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 부모에서 호출 될 때에 위임 하려면 프로젝트를 중첩 된 노드의 속성을 검색 합니다.

     부모 및 자식 프로젝트는 프로그래밍 방식으로 인스턴스화 때문에 시점에서 중첩 된 프로젝트에 대 한 속성을 설정할 수 있습니다.

    > [!NOTE]
    > 중첩 된 프로젝트에서 컨텍스트 정보를을 받고 뿐 아니라 부모 프로젝트로 있는지 확인 하 여 모든 컨텍스트에 해당 항목에 대해 질문할 수도 있습니다 [__VSHPROPID 합니다. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>)합니다. 이런 방식으로 개별 중첩된 프로젝트에 추가 동적 도움말 특성과 관련 된 메뉴 옵션을 추가할 수 있습니다.

10. 계층에 표시 하기 위해 빌드됩니다 **솔루션 탐색기** 에 대 한 호출을 사용 하 여는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> 메서드.

     계층을 통해 환경을 전달할 `GetNestedHierarchy` 솔루션 탐색기에 표시 하기 위해 계층을 형성 하 합니다. 이런 방식으로 솔루션에 프로젝트 존재 건물에 대 한 빌드 관리자가 관리할 수 있습니다 또는 소스 코드 제어에서 추가할 프로젝트의 파일 수를 알고 있습니다.

11. Project1에 대 한 모든 중첩 된 프로젝트를 만든 경우 제어 솔루션에 다시 전달 되 고 Project2에 대해이 프로세스가 반복 됩니다.

     자식 프로젝트에는 자식에 대해 중첩 된 프로젝트를 만들기 위한 동일한 프로세스가 발생 합니다. 이 경우 BuildProject1 Project1의 자식 요소인 자식 프로젝트가 있으면 이러한 만들어집니다 BuildProject1 후 Project2 하기 전에 합니다. 프로세스는 재귀 및 계층 구조 아래쪽 위쪽에서 빌드됩니다.

     사용자 솔루션 닫히거나 특정 프로젝트 자체를 다른 방법으로 하기 때문에 중첩 된 프로젝트를 닫을 때 `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, 라고 합니다. 부모 프로젝트에 대 한 호출을 래핑하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> 중첩 된 프로젝트는 닫히기 솔루션 이벤트 수신기에 알리기 위해 메서드.

다음 항목에서는 중첩 된 프로젝트를 구현 하는 경우를 고려해 야 할 다른 몇 가지 개념을 사용 하 여 처리 합니다.

- [중첩 된 프로젝트를 다시 로드 및 언로드 시 고려 사항](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [중첩 된 프로젝트에 대 한 마법사 지원](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [중첩 된 프로젝트에 대 한 명령 처리 구현](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [중첩 된 프로젝트에 대 한 항목 추가 대화 상자를 필터링 합니다.](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>참고자료

- [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [프로젝트 및 항목 템플릿을 등록합니다](../../extensibility/internals/registering-project-and-item-templates.md)
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [컨텍스트 매개 변수](../../extensibility/internals/context-parameters.md)
- [마법사 (.vsz) 파일](../../extensibility/internals/wizard-dot-vsz-file.md)