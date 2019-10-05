---
title: 연결 및 초기화 폼을 사용 하 여 워크플로 만들기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b64d1c9fbbd81a21ab268dfa29287895bd355197
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401162"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>연습: 연결 및 초기화 폼을 사용 하 여 워크플로 만들기
  이 연습에는 연결 및 초기화 폼의 사용을 통합 하는 기본 순차 워크플로 만드는 방법을 보여 줍니다. 이 SharePoint 관리자 (연결 형식)가 처음 연결할 때 및 워크플로 (양식)가 시작 될 때 워크플로에 추가 하는 매개 변수를 사용 하도록 설정 하는 ASPX 폼입니다.

 이 연습에서는 다음 요구 사항이 경비 보고서에 대 한 승인 워크플로 만들려면 사용자가 있는 시나리오를 설명 합니다.

- 워크플로 목록에 연결 하는 경우 관리자 연결 폼 경비 보고서에 대 한 금액 한도 입력 하 라는 메시지가 표시 됩니다.

- 직원 공유 문서 목록에 해당 경비 보고서를 업로드 하 고, 워크플로 시작, 워크플로 시작 양식에서 총 비용을 입력 합니다.

- 총 직원 비용 보고서 관리자의 미리 정의 된 제한을 초과 하면 직원의 관리자가 비용 보고서를 승인 하는 데는 작업이 만들어집니다. 그러나 직원의 비용 보고서 총 지출 한도 보다 작거나 인 경우 자동으로 승인 메시지를 워크플로 기록 목록에 기록 됩니다.

  이 연습에서는 다음 작업을 수행합니다.

- SharePoint 목록 정의 순차 워크플로 프로젝트 만들기 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

- 워크플로 일정을 만드는 중입니다.

- 워크플로 활동 이벤트를 처리 합니다.

- 워크플로 연결 및 초기화 폼 만들기

- 워크플로 연결 합니다.

- 수동으로 워크플로 시작 합니다.

> [!NOTE]
> 이 연습에서는 순차 워크플로 프로젝트를 사용 하지만 프로세스는 상태 시스템 워크플로 동일 합니다.
>
> 컴퓨터를 다른 이름이 나 위치 중 일부에 대해 표시할 수 있습니다는 또한는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 다음 지침에서는 사용자 인터페이스 요소입니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 해야 하는 버전 및 설정을 사용 하는 이러한 요소를 확인 합니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 및 SharePoint입니다.

- Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>SharePoint 순차 워크플로 프로젝트 만들기
 순차 워크플로 프로젝트를 먼저 만듭니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. 순차 워크플로 마지막 작업이 완료 될 때까지 순서 대로 실행 되는 일련의 단계입니다. 이 절차에서는 SharePoint에서 공유 문서 목록에 적용 되는 순차 워크플로 만듭니다. 워크플로의 마법사는 사이트 또는 목록 정의 사용 하 여 워크플로 연결할 수 있습니다 하 고 워크플로 시작 시기를 결정할 수 있습니다.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>SharePoint 순차 워크플로 프로젝트를 만들려면

1. 메뉴 모음에서 선택 **파일** > **새로 만들기** > **프로젝트** 표시 하는 **새 프로젝트** 대화 상자.

2. 확장 합니다 **SharePoint** 노드 아래 **Visual C#** 또는 **Visual Basic**를 선택한 후는 **2010** 노드.

3. 에 **템플릿** 창 선택 합니다 **SharePoint 2010 프로젝트** 프로젝트 템플릿.

4. 에 **이름** 상자에 입력 합니다 **ExpenseReport** 를 선택한 후는 **확인** 단추입니다.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

5. **디버깅에 대 한 사이트 및 보안 수준을 지정** 페이지를 선택 합니다 **팜 솔루션으로 배포** 옵션 단추를 선택한 후는 **마침** 단추를는 신뢰 수준 및 기본 사이트입니다.

     또한이 단계는 워크플로 프로젝트에만 사용할 수 있는 옵션 임 팜 솔루션으로 솔루션의 신뢰 수준을 설정 합니다.

6. **솔루션 탐색기**에서 프로젝트 노드를 선택합니다.

7. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

8. 준 **Visual C#** 또는 **Visual Basic**를 확장 합니다 **SharePoint** 노드를 선택한 후는 **2010** 노드.

9. 에 **템플릿을** 창 선택 **순차 워크플로 (팜 솔루션에만 해당)** 템플릿을 선택한 후는 **추가** 단추입니다.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

10. 에 **디버깅에 대 한 워크플로 이름을** 페이지에서 기본 이름을 그대로 (**ExpenseReport-Workflow1**). 기본 워크플로 템플릿 형식 값을 유지 (**목록 워크플로)** 합니다. **다음** 단추를 선택합니다.

11. 에 **Visual Studio 디버그 세션에서 워크플로 자동으로 연결 하 시겠습니까?** 페이지에서 선택 하는 경우 워크플로 템플릿에 자동으로 연결 하는 확인란의 선택을 취소 합니다.

     이 단계를 사용 하면 수동으로 연결 양식을 표시 하는 나중에 공유 문서 목록 사용 하 여 워크플로 연결할 수 있습니다.

12. 선택 된 **완료** 단추입니다.

## <a name="add-an-association-form-to-the-workflow"></a>워크플로 연결 양식 추가
 그런 다음 만들기를 합니다. SharePoint 관리자는 경비 보고서 문서를 사용 하 여 워크플로 처음 연결 하는 경우 표시 되는 ASPX 연결 형식입니다.

#### <a name="to-add-an-association-form-to-the-workflow"></a>연결 양식을 워크플로에 추가 하려면

1. 선택 된 **Workflow1** 노드에서 **솔루션 탐색기**합니다.

2. 메뉴 모음에서 선택 **프로젝트** > **새 항목 추가** 표시 하는 **새 항목 추가** 대화 상자.

3. 대화 상자의 트리 보기에서 하나를 확장 **Visual C#** 또는 **Visual Basic** (프로젝트 언어)에 따라 확장 합니다 **SharePoint** 노드를 선택한 후의 **2010** 노드.

4. 템플릿 목록에서 선택 합니다 **워크플로 연결 양식** 템플릿.

5. 에 **이름을** 텍스트 상자에 입력 합니다 **ExpenseReportAssocForm.aspx**합니다.

6. 선택 된 **추가** 프로젝트에 폼을 추가 하려면 단추입니다.

## <a name="designing-and-coding-the-association-form"></a>연결 폼 디자인 및 코딩
 이 절차에서는 컨트롤 및 코드를 추가 하 여 연결 폼에 기능을 소개 합니다.

#### <a name="to-design-and-code-the-association-form"></a>디자인 및 코드 연결 폼

1. 연결 양식 (ExpenseReportAssocForm.aspx)에서 찾을 합니다 `asp:Content` 가 있는 요소가 `ID="Main"`합니다.

2. 이 콘텐츠 요소의 첫 번째 줄 바로 뒤 레이블을 만들고 비용 승인 제한에서 요구 하는 텍스트 상자에 다음 코드를 추가 합니다 (*AutoApproveLimit*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. 확장을 **ExpenseReportAssocForm.aspx** 파일 **솔루션 탐색기** 해당 종속 파일을 표시 합니다.

    > [!NOTE]
    > 프로젝트에 있으면 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]를 선택 해야 합니다는 **모든 파일 보기** 이 단계를 수행 하는 단추입니다.

4. ExpenseReportAssocForm.aspx 파일에 대 한 바로 가기 메뉴를 열고 **코드 보기**합니다.

5. 대체는 `GetAssociationData` 메서드:

    ```vb
    Private Function GetAssociationData() As String
        ' TODO: Return a string that contains the association data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return Me.AutoApproveLimit.Text
    End Function
    ```

    ```csharp
    private string GetAssociationData()
    {
        // TODO: Return a string that contains the association data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.AutoApproveLimit.Text;
    }
    ```

## <a name="add-an-initiation-form-to-the-workflow"></a>워크플로 시작 양식 추가
 다음으로 사용자가 비용 보고서에 대 한 워크플로 실행할 때 표시 되는 양식을 만듭니다.

#### <a name="to-create-an-initiation-form"></a>시작 폼을 만들려면

1. 선택 된 **Workflow1** 노드에서 **솔루션 탐색기**합니다.

2. 메뉴 모음에서 선택 **프로젝트** > **새 항목 추가** 표시 합니다 **새 항목 추가** 대화 상자.

3. 대화 상자의 트리 보기에서 하나를 확장 **Visual C#** 또는 **Visual Basic** (프로젝트 언어)에 따라 확장 합니다 **SharePoint** 노드를 선택한 후의 **2010** 노드.

4. 템플릿 목록에서 선택 합니다 **워크플로 시작 양식** 템플릿.

5. 에 **이름을** 텍스트 상자에 입력 합니다 **ExpenseReportInitForm.aspx**합니다.

6. 선택 된 **추가** 프로젝트에 폼을 추가 하려면 단추입니다.

## <a name="designing-and-coding-the-initiation-form"></a>시작 폼 디자인 및 코딩
 다음으로, 컨트롤 및 코드를 추가 하 여 양식 하는 기능을 소개 합니다.

#### <a name="to-code-the-initiation-form"></a>초기화 폼 코드

1. 시작 양식 (ExpenseReportInitForm.aspx)에서 찾을 합니다 `asp:Content` 포함 하는 요소 `ID="Main"`합니다.

2. 바로이 콘텐츠 요소의 첫 번째 줄 뒤 레이블과 비용 승인 한도 표시 하는 텍스트 상자를 만들려면 다음 코드를 추가 (*AutoApproveLimit*) 다른 레이블에 연결 폼에 입력 한 및 비용 합계를 묻는 메시지를 텍스트 상자에 붙여넣습니다 (*ExpenseTotal*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. 확장을 **ExpenseReportInitForm.aspx** 파일 **솔루션 탐색기** 해당 종속 파일을 표시 합니다.

4. ExpenseReportInitForm.aspx 파일에 대 한 바로 가기 메뉴를 열고 **코드 보기**합니다.

5. 대체는 `Page_Load` 다음 예제에서는 메서드:

    ```vb
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As
      EventArgs) Handles Me.Load
        InitializeParams()
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New
          Guid(associationGuid)).AssociationData
        ' Optionally, add code here to pre-populate your form fields.
    End Sub
    ```

    ```csharp
    protected void Page_Load(object sender, EventArgs e)
    {
        InitializeParams();
        this.AutoApproveLimit.Text =
          workflowList.WorkflowAssociations[new
          Guid(associationGuid)].AssociationData;
    }
    ```

6. 대체는 `GetInitiationData` 다음 예제에서는 메서드:

    ```vb
    ' This method is called when the user clicks the button to start the workflow.
    Private Function GetInitiationData() As String
        Return Me.ExpenseTotal.Text
        ' TODO: Return a string that contains the initiation data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return String.Empty
    End Function
    ```

    ```csharp
    // This method is called when the user clicks the button to start the workflow.
    private string GetInitiationData()
    {
        // TODO: Return a string that contains the initiation data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.ExpenseTotal.Text;
    }
    ```

## <a name="cutomize-the-workflow"></a>Cutomize 워크플로
 다음으로, 워크플로 사용자 지정할 수 있습니다. 나중에 두 가지 워크플로를 연결 합니다.

#### <a name="to-customize-the-workflow"></a>워크플로 사용자 지정 하려면

1. Workflow1 프로젝트에서 열어 워크플로 디자이너에서 워크플로 표시 합니다.

2. 에 **도구 상자**, 확장을 **Windows Workflow v3.0** 노드 찾아서는 **IfElse** 활동.

3. 다음 단계 중 하나를 수행 하 여 워크플로에이 작업을 추가 합니다.

    - 에 대 한 바로 가기 메뉴를 열고 합니다 **IfElse** 활동 선택 **복사**, 아래의 줄에 대 한 바로 가기 메뉴를 열고 합니다 **onWorkflowActivated1** 워크플로 디자이너에서 활동 선택한 후 **붙여넣기**합니다.

    - 끌어서 합니다 **IfElse** 활동에서를 **도구 상자**, 아래의 줄에 연결 하 고는 **onWorkflowActiviated1** 워크플로 디자이너에서 활동.

4. 도구 상자에서 확장 합니다 **SharePoint 워크플로** 노드 찾아서는 **CreateTask** 활동.

5. 다음 단계 중 하나를 수행 하 여 워크플로에이 작업을 추가 합니다.

    - 바로 가기 메뉴를 열고 합니다 **CreateTask** 활동을 선택 **복사본**, 둘 중 하나에 대 한 바로 가기 메뉴를 열고 **여기에 작업 놓기** 내의 영역  **IfElseActivity1** 워크플로 디자이너에서 선택한 후 **붙여넣기**합니다.

    - 끌어서를 **CreateTask** 에서 작업을 **도구 상자** 둘 중 하나에 **여기에 작업 놓기** 내의 영역 **IfElseActivity1**합니다.

6. 에 **속성** 창에서 속성 값을 입력 *taskToken* 에 대 한 합니다 **CorrelationToken** 속성.

7. 확장 된 **CorrelationToken** 더하기 기호를 선택 하 여 속성 (![TreeView 더하기 기호](../sharepoint/media/plus.gif "TreeView 더하기")) 옆에 있는 합니다.

8. 드롭다운 화살표를 선택 합니다 **OwnerActivityName** 하위 속성을 설정 합니다 *Workflow1* 값입니다.

9. 선택 합니다 **TaskId** 속성을 선택한 후 줄임표 (![ASP.NET 모바일 디자이너 줄임표](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추를 표시 합니다 **바인딩 속성** 대화 상자.

10. 선택 합니다 **새 멤버에 바인딩** 탭을 선택 합니다 **필드 만들기** 옵션 단추를 선택한 후는 **확인** 단추.

11. 선택 합니다 **TaskProperties** 속성을 선택한 후 줄임표 (![ASP.NET 모바일 디자이너 줄임표](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표")) 단추를 표시 합니다  **속성 바인딩** 대화 상자.

12. 선택 합니다 **새 멤버에 바인딩** 탭을 선택 합니다 **필드 만들기** 옵션 단추를 선택한 후는 **확인** 단추.

13. 에 **도구 상자**, 확장을 **SharePoint 워크플로** 노드를 찾아서는 **LogToHistoryListActivity** 활동.

14. 다음 단계 중 하나를 수행 하 여 워크플로에이 작업을 추가 합니다.

    - 바로 가기 메뉴를 열고 합니다 **LogToHistoryListActivity** 활동을 선택 **복사**, 다른 바로 가기 메뉴를 열고 **여기에 작업 놓기** 내의영역**IfElseActivity1** 워크플로 디자이너에서 선택한 후 **붙여넣기**합니다.

    - 끌어서를 **LogToHistoryListActivity** 에서 작업을 **도구 상자**, 다른 위에 놓습니다 **여기에 작업 놓기** 영역 내에서 **IfElseActivity1** .

## <a name="add-code-to-the-workflow"></a>워크플로에 코드를 추가 합니다.
 그런 다음 기능을 제공 하는 워크플로를 코드를 추가 합니다.

#### <a name="to-add-code-to-the-workflow"></a>워크플로에 코드를 추가 하려면

1. 에 대 한 바로 가기 메뉴를 열고 합니다 **createTask1** 활동이 워크플로 디자이너에서 선택한 후 **코드 보기**.

2. 다음 메서드를 추가 합니다.

    ```vb
    Private Sub createTask1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        createTask1_TaskId1 = Guid.NewGuid
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"
        createTask1_TaskProperties1.Description = "Please approve the
          expense report"
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed"
    End Sub
    ```

    ```csharp
    private void createTask1_MethodInvoking(object sender, EventArgs e)
    {
        createTask1_TaskId1 = Guid.NewGuid();
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";
        createTask1_TaskProperties1.Description = "Please approve the
          expense report";
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed";
    }
    ```

    > [!NOTE]
    > 코드를 바꿉니다 `somedomain\\someuser` 작업은 만들 수 있는, 같은 도메인 및 사용자 이름으로 "`Office\\JoeSch`"입니다. 테스트를 위해 사용 하 여 개발 하는 계정을 사용 하 여 쉽습니다.

3. 아래는 `MethodInvoking` 메서드를 다음 예제에서는 추가:

    ```vb
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As
      ConditionalEventArgs)
        Dim approval As Boolean = False
        If (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData)) Then
            approval = True
        End If
        e.Result = approval
    End Sub
    ```

    ```csharp
    private void checkApprovalNeeded(object sender, ConditionalEventArgs
      e)
    {
        bool approval = false;
        if (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData))
        {
            approval = true;
        }
        e.Result = approval;
    }
    ```

4. 워크플로 디자이너에서 선택 합니다 **ifElseBranchActivity1** 활동입니다.

5. 에 **속성** 창의 드롭다운 화살표를 선택 합니다 **조건** 속성을 설정을 *코드 조건을* 값.

6. 확장 합니다 **조건을** 더하기 기호를 선택 하 여 속성 (![TreeView 더하기 기호](../sharepoint/media/plus.gif "TreeView 더하기 기호")) 옆에 해당 값 설정한 후 *checkApprovalNeeded* .

7. 워크플로 디자이너에서 바로 가기 메뉴를 열고 합니다 **logToHistoryListActivity1** 활동을 선택한 후 **처리기 생성** 에 대 한 빈 메서드를 생성 하는 `MethodInvoking` 이벤트입니다.

8. 대체는 `MethodInvoking` 다음을 사용 하 여 코드:

    ```vb
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto
          approved for " + workflowProperties.InitiationData)
    End Sub
    ```

    ```csharp
    private void logToHistoryListActivity1_MethodInvoking(object sender,
      EventArgs e)
    {
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was
          auto approved for " + workflowProperties.InitiationData;
    }
    ```

9. 선택 된 **F5** 프로그램을 디버깅 하려면 키입니다.

     이 응용 프로그램을 컴파일하고, 패키지, 배포, 해당 기능을 활성화, 재활용 합니다 [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] 응용 프로그램 풀 및 위치의 브라우저에 지정 된 다음 시작 합니다 **사이트 Url** 속성입니다.

## <a name="associating-the-workflow-to-the-documents-list"></a>문서 목록에 워크플로 연결
 다음으로, 사용 하 여 워크플로 연결 하 여 워크플로 연결 폼을 표시 합니다 **SharedDocuments** SharePoint 사이트의 목록입니다.

#### <a name="to-associate-the-workflow"></a>워크플로 연결

1. 선택 된 **Shared Documents** 빠른 실행 모음에 대 한 링크입니다.

2. 선택 합니다 **라이브러리** 링크를 **라이브러리 도구** 탭을 선택한 후는 **라이브러리 설정** 리본 단추.

3. **사용 권한 및 관리** 섹션을 선택 합니다 **워크플로 설정을** 링크를 선택한는 **워크플로 추가** 링크를 **워크플로** 페이지.

4. 워크플로 설정 페이지의 맨 위 목록에서 선택 합니다 **ExpenseReport-Workflow1** 템플릿.

5. 다음 필드에 입력 **ExpenseReportWorkflow** 를 선택 합니다 **다음** 단추입니다.

     이 사용 하 여 워크플로 연결 합니다 **Shared Documents** 목록 및 워크플로 연결 폼을 표시 합니다.

6. 에 **자동 승인 제한** 텍스트 상자에 입력 합니다 **1200** 를 선택한 후는 **워크플로 연결** 단추입니다.

## <a name="start-the-workflow"></a>워크플로 시작 합니다.
 다음으로, 문서 중 하나에 워크플로 연결 합니다 **Shared Documents** 목록 워크플로 시작 양식을 표시 합니다.

#### <a name="to-start-the-workflow"></a>워크플로 시작 하려면

1. SharePoint 페이지에서 선택 합니다 **홈** 단추입니다.

2. 선택 된 **Shared Documents** 표시할 빠른 실행 모음에 대 한 링크는 **Shared Documents** 목록.

3. 선택 합니다 **문서** 링크를 **라이브러리 도구** 페이지의 맨 위에 있는 탭을 선택한를 **문서 업로드** 에 새 문서를 업로드 하려면 리본에서 단추를 **Shared Documents** 목록입니다.

4. 에 **문서 업로드** 대화 상자를 선택 합니다 **찾아보기** 단추, 문서 파일을 선택는 **열기** 단추를 선택한 후를 **확인** 단추입니다.

     이 대화 상자에서 문서에 대 한 설정을 변경할 수 있지만 선택 하 여 기본값으로 그대로 합니다 **저장할** 단추입니다.

5. 업로드 된 문서를 선택 하 고 표시를 선택한 후 드롭다운 화살표를 **워크플로** 항목입니다.

6. ExpenseReportWorkflow 옆에 있는 이미지를 선택 합니다.

     워크플로 시작 양식을 표시 됩니다. (값에 표시 되는 **자동 승인 제한** 상자는 읽기 전용 연결 양식에서 입력 되었습니다.)

7. 에 **비용 합계** 텍스트 상자에 입력 합니다 **1600**를 선택한 후는 **워크플로 시작** 단추입니다.

     이 표시 합니다 **Shared Documents** 목록을 다시 합니다. 이라는 새 열 **ExpenseReportWorkflow** 값을 가진 **완료** 워크플로 시작 항목으로 추가 됩니다.

8. 업로드 된 문서 옆에 있는 드롭다운 화살표를 선택한 다음 선택 합니다 **워크플로** 워크플로 상태 페이지에 표시할 항목입니다. 선택 된 **완료 됨** 값 **완료 워크플로**합니다. 작업은 아래에 **작업** 섹션입니다.

9. 작업 세부 정보를 표시 하기 위해 작업의 제목을 선택 합니다.

10. 로 다시 이동 합니다 **SharedDocuments** 나열 하 고 동일한 문서 또는 다른 이름을 사용 하 여 워크플로 다시 시작 합니다.

11. 연결 페이지에서 입력 된 금액 보다 작거나 같은 시작 페이지에서 금액을 입력 하십시오 (**1200**).

     이 문제가 발생 하면 작업 대신 기록 목록에서 항목이 생성 됩니다. 항목을 표시 합니다 **워크플로 기록** 워크플로 상태 페이지의 섹션입니다. 에 메시지를 확인 합니다 **결과** 기록 이벤트의 열입니다. 에 입력 된 텍스트를 포함 하는 `logToHistoryListActivity1.MethodInvoking` 자동으로 승인 된 금액을 포함 하는 이벤트입니다.

## <a name="next-steps"></a>다음 단계
 다음이 항목에서는 워크플로 템플릿을 만드는 방법에 대 한 자세한 수 있습니다.

- SharePoint 워크플로에 대 한 자세한 내용은 참조 하세요 [Windows SharePoint Services에서 워크플로](http://go.microsoft.com/fwlink/?LinkID=166275)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 워크플로 솔루션 만들기](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [연습: 워크플로에 응용 프로그램 페이지 추가](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
