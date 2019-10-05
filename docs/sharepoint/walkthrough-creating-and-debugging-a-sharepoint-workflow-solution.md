---
title: SharePoint 워크플로 솔루션을 디버그 및 만들기
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 51682ba54d6a6ae0698ade6bb52d5972cd63111f
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401052"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>연습: 만들고 SharePoint 워크플로 솔루션을 디버그 합니다.
  이 연습에는 기본 순차 워크플로 템플릿을 만드는 방법을 보여 줍니다. 워크플로 문서를 검토 했는지 여부를 결정 하는 공유 문서 라이브러리의 속성을 확인 합니다. 문서를 검토 하는 경우 워크플로가 완료 됩니다.

 이 연습에서는 다음 작업을 수행합니다.

- SharePoint 목록 정의 순차 워크플로 프로젝트 만들기 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

- 워크플로 활동을 만드는 중입니다.

- 워크플로 활동 이벤트를 처리 합니다.

> [!NOTE]
> 이 연습에서는 순차 워크플로 프로젝트를 사용 하지만 프로세스는 상태 시스템 워크플로 프로젝트에 대 한 동일 합니다.
>
> 또한 컴퓨터에서에서 표시할 수 있습니다 다른 이름이 나 위치 일부 Visual Studio 사용자 인터페이스 요소 다음 지침을 합니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- 지원되는 Microsoft Windows 및 SharePoint 버전.

- Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>SharePoint 공유 문서 라이브러리에 속성 추가
 문서에서의 검토 상태를 추적 하는 **공유 문서** 라이브러리를 만들겠습니다 공유 문서에 대 한 새 속성을 세 가지 SharePoint 사이트에서: `Status`를 `Assignee`, 및 `Review Comments`합니다. 이러한 속성에 정의 된 **Shared Documents** 라이브러리입니다.

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>문서 라이브러리 SharePoint 공유에 속성 추가

1. 예: http:// SharePoint 사이트를 열고\<시스템 이름 > / 웹 브라우저에서 SitePages/Home.aspx 합니다.

2. 빠른 실행 모음에서 선택 **SharedDocuments**합니다.

3. 선택 **라이브러리** 에 **라이브러리 도구** 리본 메뉴를 선택한 후는 **열 만들기** 새 열을 만들려면 리본의 단추입니다.

4. 열의 이름을 **Document Status**, 해당 유형을 설정 **선택 (메뉴에서 선택)** 는 다음 세 가지 선택 옵션을 지정 하 고 선택한 합니다 **확인** 단추:

    - **검토 필요**

    - **검토 완료**

    - **요청 된 변경 내용**

5. 두 개 이상의 열을 만들고 이름을 **담당자** 하 고 **검토 주석은**합니다. 여러 줄 텍스트의 텍스트 한 줄으로 담당자 열 형식 및 검토 주석 열 형식이 설정 합니다.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>체크 아웃을 하지 않고도 편집할 문서를 사용 하도록 설정
 체크 아웃 하지 않고 문서를 편집할 수 있도록 워크플로 서식 파일을 테스트 하는 것이 쉽습니다. 다음 절차에서는 SharePoint 사이트는 사용할 수 있도록 구성할 수 있습니다.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>문서 체크 아웃 하지 않고 편집을 사용 하도록 설정 하려면

1. 빠른 실행 모음에서 선택 합니다 **Shared Documents** 링크 합니다.

2. 에 **라이브러리 도구** 리본에서 선택 합니다 **라이브러리** 탭을 선택한 다음를 **라이브러리 설정** 표시 하려면 단추를 **문서 라이브러리 설정** 페이지.

3. **일반 설정** 섹션을 선택 합니다 **버전 관리 설정** 표시 하려면 링크를 **버전 관리 설정** 페이지.

4. 확인에 대 한 설정을 **문서를 편집 하려면 먼저 체크 아웃 해야** 됩니다 **No**. 되지 않은 경우 변경 **없음** 를 선택 합니다 **확인** 단추.

5. 브라우저를 닫습니다.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>SharePoint 순차 워크플로 프로젝트 만들기
 순차 워크플로 마지막 작업이 완료 될 때까지 순서 대로 실행 되는 일련의 단계입니다. 이 절차에서는 공유 문서 목록에 적용 되는 순차 워크플로 만듭니다. 워크플로 마법사에는 사이트 정의 또는 목록 정의 사용 하 여 워크플로 연결할 수 있습니다 하 고 워크플로 시작 시기를 결정할 수 있습니다.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint 순차 워크플로 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 선택 **파일** > **새로 만들기** > **프로젝트** 표시 하는 **새 프로젝트** 대화 상자.

3. 확장 합니다 **SharePoint** 노드 아래 **Visual C#** 또는 **Visual Basic**를 선택한 후는 **2010** 노드.

4. 에 **템플릿을** 창 선택 합니다 **SharePoint 2010 프로젝트** 템플릿.

5. 에 **이름** 상자에 입력 합니다 **MySharePointWorkflow** 를 선택한 후는 **확인** 단추입니다.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

6. **디버깅에 대 한 사이트 및 보안 수준을 지정** 페이지를 선택 합니다 **팜 솔루션으로 배포** 옵션 단추를 선택한 후는 **마침** 단추를는 신뢰 수준 및 기본 사이트입니다.

     이 단계는 팜 솔루션에 워크플로 프로젝트에만 사용할 수 있는 옵션으로 솔루션의 신뢰 수준을 설정합니다. 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)합니다.

7. **솔루션 탐색기**, 프로젝트 노드를 선택한 다음, 메뉴 모음에서 **프로젝트** > **새 항목 추가**합니다.

8. 준 **Visual C#** 또는 **Visual Basic**를 확장 합니다 **SharePoint** 노드를 선택한 후는 **2010** 노드.

9. 에 **템플릿** 창 선택 합니다 **순차 워크플로 (팜 솔루션에만 해당)** 템플릿을 선택한 후는 **추가** 단추.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

10. 에 **디버깅에 대 한 워크플로 이름을** 페이지에서 기본 이름을 그대로 (**MySharePointWorkflow-Workflow1**). 기본 워크플로 템플릿 형식 값을 유지 **목록 워크플로**를 선택 합니다 **다음** 단추입니다.

11. 에 **Visual Studio 디버그 세션에서 워크플로 자동으로 연결 하 시겠습니까?** 페이지를 선택 합니다 **다음** 모두 기본 설정을 적용 하려면 단추.

     이 단계는 자동으로 공유 문서 라이브러리를 사용 하 여 워크플로 연결합니다.

12. 에 **워크플로 시작 방법에 대 한 조건을 지정** 페이지에서 기본 옵션에서 선택한 합니다 **워크플로 시작 방법을 선택 하십시오?** 선택한 섹션는 **마침** 단추입니다.

     이 페이지를 사용 하면 워크플로가 시작 되는 경우를 지정할 수 있습니다. 기본적으로 워크플로 시작 하거나 사용자의 SharePoint 워크플로 연관 된 항목을 만들면가 수동으로 시작 합니다.

## <a name="create-workflow-activities"></a>워크플로 작업 만들기
 워크플로에 하나 이상의 *활동* 수행 하는 작업을 나타냅니다. 워크플로 디자이너를 사용 하 여 워크플로에 대 한 작업을 정렬 합니다. 이 절차에서는 두 작업 워크플로에 추가 됩니다. HandleExternalEventActivity 및 OnWorkFlowItemChanged 합니다. 이러한 활동의 문서 검토 상태를 모니터링 합니다 **Shared Documents** 목록

#### <a name="to-create-workflow-activities"></a>워크플로 작업을 만들려면

1. 워크플로 디자이너에서 워크플로 표시 합니다. 없는 경우 다음 엽니다 **Workflow1.cs** 하거나 **Workflow1.vb** 에서 **솔루션 탐색기**합니다.

2. 디자이너에서 선택 합니다 **OnWorkflowActivated1** 활동입니다.

3. 에 **속성** 창 입력 **onWorkflowActivated** 옆에 **호출** 속성을 선택한 다음 Enter 키입니다.

     코드 편집기가 열리고 onWorkflowActivated 라는 이벤트 처리기 메서드를 Workflow1 코드 파일에 추가 됩니다.

4. 워크플로 디자이너로 다시 전환, 도구 상자를 열고 및 차례로 확장 합니다 **Windows Workflow v3.0** 노드.

5. 에 **Windows Workflow v3.0** 노드의 합니다 **도구 상자**, 다음 단계 집합 중 하나를 수행:

    1. 바로 가기 메뉴를 열고 합니다 **하는 동안** 활동을 선택한 후 **복사**합니다. 워크플로 디자이너에서 아래의 줄에 대 한 바로 가기 메뉴를 열고 합니다 **onWorkflowActivated1** 활동을 선택한 후 **붙여넣기**합니다.

    2. 끌어서를 **하는 동안** 활동에서는 **도구 상자** 워크플로 디자이너로 작업 아래의 줄에 연결 하 고는 **onWorkflowActivated1** 활동.

6. 선택 된 **WhileActivity1** 활동입니다.

7. 에 **속성** 창에서 **조건** 코드 조건입니다.

8. 확장을 **조건** 속성을 입력 **isWorkflowPending** 자식 옆에 있는 **조건** 속성 Enter 키를 선택 하 고 합니다.

     코드 편집기가 열리고 메서드가 isWorkflowPending Workflow1 코드 파일에 추가 됩니다.

9. 워크플로 디자이너로 다시 전환, 도구 상자를 열고 및 차례로 확장 합니다 **SharePoint 워크플로** 노드.

10. 에 **SharePoint 워크플로** 노드의 합니다 **도구 상자**, 다음 단계 집합 중 하나를 수행:

    - 바로 가기 메뉴를 열고 합니다 **OnWorkflowItemChanged** 활동을 선택한 후 **복사**합니다. 워크플로 디자이너에서 내 줄에 대 한 바로 가기 메뉴를 열고 합니다 **whileActivity1** 활동을 선택한 후 **붙여넣기**합니다.

    - 끌어서 합니다 **OnWorkflowItemChanged** 활동에서를 **도구 상자** 워크플로 디자이너에 활동 내에서 줄에 연결 하 고는 **whileActivity1** 활동.

11. 선택 된 **onWorkflowItemChanged1** 활동입니다.

12. 에 **속성** 창에서 다음 표에 나와 있는 것 처럼 속성을 설정 합니다.

    |속성|값|
    |--------------|-----------|
    |**CorrelationToken**|**workflowToken**|
    |**호출**|**onWorkflowItemChanged**|

## <a name="handle-activity-events"></a>활동 이벤트를 처리 합니다.
 마지막으로, 각 작업에서 문서 상태를 확인 합니다. 문서를 검토 하는 경우 워크플로가 완료 됩니다.

#### <a name="to-handle-activity-events"></a>활동 이벤트를 처리 하려면

1. *Workflow1.cs* 또는 *Workflow1.vb*, 위쪽에 다음 필드를 추가 합니다 `Workflow1` 클래스입니다. 이 필드는 워크플로 완료할 지 여부를 확인 하려면 작업에서 사용 됩니다.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. 다음 메서드를 `Workflow1` 클래스에 추가합니다. 값을 확인 하는이 메서드는 `Document Status` 문서를 검토 했는지 여부를 결정 하는 문서 목록의 속성입니다. 경우는 `Document Status` 속성이로 설정 되어 `Review Complete`, 해당 `checkStatus` 메서드 집합 합니다 `workflowPending` 필드를 **false** 워크플로 완료할 준비가 되었음을 나타내기 위해.

    ```vb
    Private Sub checkStatus()
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then
            workflowPending = False
        End If
    End Sub
    ```

    ```csharp
    private void checkStatus()
    {
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")
        workflowPending = false;
    }
    ```

3. 다음 코드를 추가 합니다 `onWorkflowActivated` 및 `onWorkflowItemChanged` 메서드를 호출 하는 `checkStatus` 메서드. 워크플로가 시작 되는 경우, `onWorkflowActivated` 메서드 호출을 `checkStatus` 문서를 검토 했는지 이미 있는지 여부를 결정 하는 방법입니다. 하는 경우 해당 검토 되지 않았습니다., 워크플로가 계속 됩니다. 문서를 저장 하는 경우는 `onWorkflowItemChanged` 메서드 호출을 `checkStatus` 방법 다시 문서를 검토 했는지 여부를 결정 합니다. 동안 합니다 `workflowPending` 필드 설정 됩니다 **true**, 워크플로가 계속 실행 됩니다.

    ```vb
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub

    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)
        checkStatus()
    End Sub
    ```

    ```csharp
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }

    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)
    {
        // Check the status.
        checkStatus();
    }
    ```

4. 다음 코드를 추가 합니다 `isWorkflowPending` 의 상태를 확인 하는 메서드는 `workflowPending` 속성입니다. 문서를 저장할 때마다 합니다 **whileActivity1** 작업 호출을 `isWorkflowPending` 메서드. 이 메서드는 검사를 <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> 의 속성을 <xref:System.Workflow.Activities.ConditionalEventArgs> 확인할 개체 있는지 여부를 **WhileActivity1** 활동 계속할지 또는 완료 합니다. 속성 설정 된 경우 **true**, 작업을 계속 합니다. 이 고, 그렇지 작업이 완료 되 고 워크플로가 완료 합니다.

    ```vb
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)
        e.Result = workflowPending
    End Sub
    ```

    ```csharp
    private void isWorkflowPending(object sender, ConditionalEventArgs e)
    {
        e.Result = workflowPending;
    }
    ```

5. 프로젝트를 저장합니다.

## <a name="test-the-sharepoint-workflow-template"></a>SharePoint 워크플로 템플릿을 테스트합니다
 디버거를 시작할 때 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 워크플로 템플릿을 SharePoint 서버에 배포 하 고 사용 하 여 워크플로 연결 합니다 **Shared Documents** 목록입니다. 워크플로 테스트 하려면 문서에서 워크플로 인스턴스를 시작 합니다 **Shared Documents** 목록입니다.

#### <a name="to-test-the-sharepoint-workflow-template"></a>SharePoint 워크플로 템플릿을 테스트 하려면

1. *Workflow1.cs* 하거나 *Workflow1.vb*, 옆에 중단점을 설정 합니다 **onWorkflowActivated** 메서드.

2. 선택 된 **F5** 키를 빌드하고 솔루션을 실행 합니다.

     SharePoint 사이트가 나타납니다.

3. SharePoint의 탐색 창에서 선택 합니다 **Shared Documents** 링크 합니다.

4. 에 **Shared Documents** 페이지를 선택 합니다 **문서** 링크를 **라이브러리 도구** 탭을 선택한 다음를 **문서 업로드** 단추 .

5. 에 **문서 업로드** 대화 상자를 선택 합니다 **찾아보기** 단추, 문서 파일을 선택는 **열기** 단추를 선택한 후를 **확인** 단추입니다.

     이 선택한 문서를 업로드 합니다 **Shared Documents** 목록 및 워크플로 시작 합니다.

6. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에 디버거가 중단점에서 멈추면 옆에 확인을 `onWorkflowActivated` 메서드.

7. 선택 된 **F5** 계속 실행 하는 키입니다.

8. 여기서 문서에 대 한 설정을 변경할 수 있지만 기본값을 그대로 이제 선택 하 여 합니다 **저장할** 단추입니다.

     이 반환 하는 **Shared Documents** 기본 SharePoint 웹 사이트의 페이지입니다.

9. 에 **Shared Documents** 페이지에서 아래 값을 **MySharePointWorkflow-Workflow1** 열으로 설정 됩니다 **진행**. 이 문서 검토 대기 중이 고 워크플로 진행에서 중임 나타냅니다.

10. 에 **Shared Documents** 페이지, 문서를 선택 표시를 선택한 후 화살표를 선택 합니다 **속성 편집** 메뉴 항목입니다.

11. 설정 **Document Status** 하 **Review Complete**를 선택한 후는 **저장** 단추입니다.

     이 반환 하는 **Shared Documents** 기본 SharePoint 웹 사이트의 페이지입니다.

12. 에 **Shared Documents** 페이지에서 아래 값을 **Document Status** 열으로 설정 됩니다 **Review Complete**. 새로 고침를 **Shared Documents** 페이지 및 확인 아래 값을 **MySharePointWorkflow-Workflow1** 열으로 설정 됩니다 **완료**합니다. 이 나타내는 워크플로가 완료 되 고 문서가 검토 되었습니다.

## <a name="next-steps"></a>다음 단계
 다음이 항목에서는 워크플로 템플릿을 만드는 방법에 대 한 자세한 수 있습니다.

- SharePoint 워크플로 활동에 대 한 자세한 내용은 참조 하세요 [SharePoint Foundation에 대 한 워크플로 작업](http://go.microsoft.com/fwlink/?LinkId=178992)합니다.

- Windows Workflow Foundation 활동에 대 한 자세한 내용은 참조 하세요 [Namespace System.Workflow.Activities](http://go.microsoft.com/fwlink/?LinkId=178993)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 워크플로 솔루션 만들기](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
