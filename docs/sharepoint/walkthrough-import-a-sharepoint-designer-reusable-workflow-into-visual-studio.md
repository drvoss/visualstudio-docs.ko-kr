---
title: '연습: SharePoint Designer의 재사용 가능한 워크플로 Visual Studio로 가져오기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.WSPImport.ImportWF
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing reusable workflows
- reusable workflows [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c7d1373339fac4768e2af1eda5770d5058ae8078
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446598"
---
# <a name="walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio"></a>연습: Visual Studio에 SharePoint Designer의 재사용 가능한 워크플로 가져오기
  이 연습에서는 SharePoint Designer 2010에서 만든 재사용 가능한 워크플로 가져오는 방법을 보여는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 워크플로 프로젝트입니다.

 SharePoint Designer에서 만든 워크플로 또는 *선언적 워크플로*, 이루어진 [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] 코드 대신 문입니다. SharePoint Designer 2010 소개 *재사용 가능한 워크플로*, SharePoint 사이트의 다른 목록에서 사용할 수 있는 이식 가능한 선언적 워크플로 합니다.

 만든 워크플로 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], 순차 및 상태 시스템 워크플로와 같은 이라고 *워크플로 코드*합니다. 코드 워크플로 XML 파일, 코드 모듈에는 사용자 워크플로의 동작으로 구성 됩니다.

 Visual Studio에서는 SharePoint Designer 2010에서 만든 다시 사용할 수 있는 워크플로를 가져와서 SharePoint 사이트에서 사용할 수 있도록 코드 워크플로로 변환할 수 있습니다.

 이 연습에서는 다음 작업을 수행합니다.

- SharePoint Designer에서 간단 하 고 재사용 가능한 워크플로 만드는 중입니다.

- SharePoint Designer 재사용 가능한 워크플로를 내보내는 *.wsp* 파일 및 SharePoint에 있습니다.

- 가져오기의 *.wsp* 파일 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 재사용 가능한 워크플로 가져오기 프로젝트를 사용 하 여 합니다.

- 코드를 추가 하 여 워크플로 변경 합니다.

- SharePoint 사이트에서 가져온된 워크플로 사용합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 및 SharePoint입니다.

- Visual Studio.

- Microsoft [!INCLUDE[TLA2#tla_office](../sharepoint/includes/tla2sharptla-office-md.md)] SharePoint Designer 2010.

## <a name="create-target-sharepoint-subsites"></a>대상 SharePoint 하위 사이트 만들기
 먼저 두 개의 새 SharePoint 하위 사이트를 만듭니다: 변환 된 워크플로 호스트 하는 다른 SharePoint Designer에서 재사용 가능한 워크플로 호스트를 하나입니다.

#### <a name="to-create-sharepoint-subsites"></a>SharePoint 하위 사이트를 만들려면

1. SharePoint Designer 2010의 메뉴 모음에서 선택 **파일** > **새 웹 사이트**합니다.

2. 에 **새 웹 사이트** 대화 상자에서 워크플로 만들거나 http://의 값을 사용 하려는 SharePoint 사이트로<em>SystemName</em>/ 선택한 후는 **확인** 단추입니다.

    홈 페이지가 나타납니다.

3. 에 **하위** 섹션을 선택 합니다 **새로 만들기** 단추.

4. 에 **새로 만들기** 대화 상자에서 **SharePoint 템플릿** 왼쪽 창의 목록에서 선택한 **팀 사이트** 오른쪽 창의 목록에서.

5. 에 **웹 사이트의 위치를 지정** 상자에 단어를 대체 **하위** URL의 **SPD1**를 선택한 후는 **확인** 단추입니다.

    SharePoint Designer로 새 하위를 열립니다. SharePoint Designer의이 인스턴스를 닫고 다시 인스턴스로 이동 하는 첫 번째 (최상위 사이트).

6. 두 번째 하위 단어를 대체 합니다.이 기간을 설정 하려면 3-5 단계를 반복 **subsite** 에 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 사용 하 여 **SPD2**합니다.

## <a name="create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer의 재사용 가능한 워크플로 만들기
 SharePoint에이 예를 사용할 수 있는 재사용 가능한 워크플로 포함 되어 있지 않으므로, 만들어집니다. 이 간단한 워크플로 특정 타이틀에 있는 태스크 목록에 새 작업을 입력 하는 경우 해당 사용자에 게 작업이 할당 됩니다.

#### <a name="to-create-a-sharepoint-designer-reusable-workflow"></a>SharePoint Designer의 재사용 가능한 워크플로 만들려면

1. 에 **하위 사이트** 섹션을 선택 합니다 **SPD1** 수정할 사이트.

2. 리본에서 선택 합니다 **재사용 가능한 워크플로** 단추입니다.

     다시 사용할 수 있는 워크플로 만들기 마법사가 나타납니다.

3. 에 **이름을** 상자에 입력 합니다 **SPD Task Workflow**합니다.

4. 에 **Content-type** 목록에서 선택 **작업**를 선택한 후는 **확인** 단추.

     워크플로에서는 SharePoint Designer 워크플로 디자이너에서 열립니다.

5. 워크플로 디자이너에서 1 단계에서 선택한 다음 리본 메뉴를 선택 합니다 **조건을** 단추입니다.

6. 조건 목록에서 선택 **현재 항목 필드 값이 같으면**합니다.

     이 단계에서는 라고 하는 조건을 추가 **값이 같은 경우**합니다.

7. 에 **값이 같은 경우** 조건를 선택 합니다 **필드** 링크.

8. 값의 목록에서 선택 **Title**합니다.

9. 에 **값이 같은 경우** 조건를 선택 합니다 **값** 링크.

10. 상자에서 입력 **새 작업**합니다.

     이제 조건문 **하는 경우 현재 항목: Title이 새 작업과 일치**합니다.

11. 고 조건문 아래의 줄을 선택한 다음 리본 메뉴를 선택 합니다 **동작** 단추입니다.

12. 작업 목록에서 선택 **현재 항목의 필드 집합**합니다.

13. 에 **집합 필드를 값** 작업을 선택 합니다 **필드** 링크를 선택한 다음 목록에서 선택 **에 할당 된**.

14. 에 **집합 필드를 값** 작업을 선택 합니다 **값** 링크를 선택한 다음, 기존 사용자 및 그룹의 목록에서 **항목을 만든 사용자**합니다.

15. 선택 된 **추가** 단추를 선택한 후 합니다 **확인** 단추입니다.

     이제이 작업 문은 **집합 할당을 현재 항목: CreatedBy를**입니다.

## <a name="save-and-deploy-the-reusable-workflow"></a>저장 하 고 재사용 가능한 워크플로 배포 합니다.
 때문에 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 만 가져올 수 있습니다 *.wsp* 파일을 다시 사용할 수 있는 워크플로로 저장 해야 합니다는 *.wsp* 파일과로 가져오기 전에를 SharePoint에 배포할 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

> [!IMPORTANT]
> 다음 절차를 수행 하는 런타임 오류가 발생 하는 경우 SharePoint 사이트에 액세스할 수 있는 시스템에서 절차를 수행 해야 합니다.

#### <a name="to-save-and-deploy-the-reusable-workflow"></a>저장 하 고 재사용 가능한 워크플로 배포

1. SharePoint Designer의 맨 위에 있는 선택 합니다 **저장** 여 진행 상황을 저장 하려면 단추를 선택한 합니다 **게시** 워크플로를 배포 하는 단추를 **SPD1** SharePoint 사이트 .

2. 탐색 창에서 선택 합니다 **워크플로** 개체입니다.

3. 아래 **재사용 가능한 워크플로**, 선택 **SPD Task Workflow**합니다.

4. 리본에서 선택 합니다 **템플릿으로 저장** 으로 워크플로 저장 하려면 단추를 *.wsp* 파일입니다.

5. 엽니다는 **SPD1** 보려면 브라우저에서 SharePoint 사이트를 *.wsp* SharePoint에서 파일입니다.

6. 빠른 실행 모음에서 선택 합니다 **라이브러리** 링크 합니다.

7. 에 **문서 라이브러리** 섹션을 선택 합니다 **사이트 자산** 링크 합니다.

     합니다 **SPD Task Workflow** 파일은 기타 사이트 자산을 사용 하 여 나열 됩니다.

8. 파일 목록에서 해당 파일의 이름을 선택합니다.

9. 에 **파일 다운로드** 대화 상자를 선택 합니다 **저장** 저장 하려면 단추를 *.wsp* 로컬 시스템에서 파일.

## <a name="import-the-wsp-file-into-visual-studio"></a>Visual Studio에.wsp 파일 가져오기
 가져오기의 *.wsp* 파일 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 재사용 가능한 워크플로 가져오기 프로젝트를 사용 하 여 합니다. 이 프로젝트에서 다시 사용할 수 있는 선언적 워크플로 코드 워크플로로 워크플로 변환합니다. 워크플로 변환한 후에 해당 동작을 수정 하려면 코드를 사용 합니다.

#### <a name="to-import-a-workflow-from-a-wsp-file-and-modify-it"></a>.Wsp 파일에서 워크플로 가져오고 수정

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 메뉴 모음에서 **파일** > **New** > **프로젝트**합니다.

2. 에 **새 프로젝트** 대화 상자에서 **SharePoint** 노드 아래의 **Visual C#** 또는 **Visual Basic**를 선택한 다음 합니다 **2010** 노드.

3. 에 **템플릿** 창 선택 합니다 **다시 사용할 수 있는 SharePoint 2010 워크플로 가져오기** 템플릿을 파일로 프로젝트의 이름을 **WorkflowImportProject1**, 선택한 후는 **확인** 단추입니다.

    SharePoint 사용자 지정 마법사가 나타납니다.

4. 에 **디버깅에 대 한 사이트 및 보안 수준을 지정** 페이지에서 입력 합니다 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 이전에 만든 두 번째 SharePoint 하위 사이트에 대 한: http://<em>시스템 이름</em>/SPD2 합니다.

5. 에 **이 SharePoint 솔루션의 신뢰 수준을?** 섹션을 선택 합니다 **팜 솔루션으로 배포** 옵션 단추를 선택한 후는 **다음** 단추.

    샌드박스가 적용 된에 대 한 자세한 내용은 참조는 팜 솔루션에 비해 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)합니다.

6. 에 **새 프로젝트 소스 지정** 페이지에서 이전에 저장 된 시스템의 위치로 이동 합니다 *.wsp* 파일, 파일을 열고, 선택한를 **다음** 단추입니다.

   > [!NOTE]
   > 선택는 **완료** 에서 사용 가능한 모든 항목을 가져오려는 단추를 *.wsp* 파일.

    그러면 재사용 가능한 워크플로 가져오기에 사용할 수 있는 목록이 표시 됩니다.

7. **가져올 항목 선택** 상자를 선택 합니다 **SPD Task Workflow** 워크플로 선택한 후는 **마침** 단추.

    프로젝트에 가져오기 작업이 완료 되 면 **WorkflowImportProject1** 라는 워크플로 포함 하는 데 만들어집니다 **SPD_Workflow_TestFT**합니다. 이 폴더에는 워크플로의 정의 파일 *Elements.xml* 및 워크플로 디자이너 파일 (*.xoml*). 디자이너에 두 파일이: 규칙 (.rules) 파일과 코드 숨김 파일 (하거나 *.cs* 또는 *.vb*프로젝트의 프로그래밍 언어에 따라).

8. **솔루션 탐색기**를 삭제 합니다 **기타 가져온 파일** 폴더입니다.

9. 에 *Elements.xml* 파일을 삭제 `InstantiationURL="_layouts/IniErkflIP.sspx"`합니다.

10. **솔루션 탐색기**, 선택 **WorkflowImportProject1**를 선택한 다음 메뉴 모음에서 **프로젝트** > **시작 프로젝트로 설정**  설정할 **WorkflowImportProject1** 시작 항목으로 합니다.

     이 프로젝트를 디버깅할 때 즉시 목록이 표시 됩니다.

11. 때문에 합니다 **다시 사용할 수 있는 SharePoint 2010 워크플로 가져오기** 템플릿은 가져온된 워크플로에 대 한 연결 속성 값을 가져오지 않는, 직접 입력 해야 합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

    1. **솔루션 탐색기**를 선택 합니다 **SPD_Workflow_TestFT** 노드.

    2. 줄임표 (![ASP.NET 모바일 디자이너 줄임표](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표"))와 같은 목록 속성 중 하나 옆의 단추를 **대상 목록** 속성입니다.

    3. SharePoint 사용자 지정 마법사에서 누락 값을 입력 하 고 다음을 선택 합니다 **완료** 단추입니다.

12. .Xoml 파일을 선택한 다음, 메뉴 모음에서 **뷰** > **디자이너** 워크플로 디자이너에서 가져온된 워크플로 볼 수 있습니다.

13. 에 **Windows Workflow v3.0** 노드의 합니다 **도구 상자**, 다음 단계 중 하나를 수행:

    - 바로 가기 메뉴를 열고 합니다 **코드** 활동을 선택한 후 **복사**합니다. 워크플로 디자이너에서 아래의 줄에 대 한 바로 가기 메뉴를 열고 합니다 **SequenceActivity1** 활동을 선택한 후 **붙여넣기**합니다.

    - 끌어서 합니다 **코드** 활동에서를 **도구 상자** 워크플로 디자이너에 아래의 줄에 연결 하 고는 **SequenceActivity1** 활동.

      명명 된 워크플로 디자이너에 활동 추가 **CodeActivity1**합니다. 이 작업에서는 사용자가 워크플로 시작 하는 경우 알림 목록에 공지를 만드는 코드 작업을 추가 합니다.

14. 다음 단계 중 하나를 수행합니다.

    - 두 번 클릭 **CodeActivity1** 이벤트 처리기를 코드를 보고 합니다.

    - 에 **속성** 창에 대 한 **CodeActivity1**의 값을 설정 합니다 **ExecuteCode** 속성을 **codeActivity_ExecuteCode**.

15. 기존 아래에 다음을 추가 **를 사용 하 여** 하거나 **Imports** 문:

     [!code-csharp[SP_SPDWFImport#1](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#1)]
     [!code-vb[SP_SPDWFImport#1](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#1)]

16. 대체 `codeActivity1_ExecuteCode` 다음을 사용 하 여:

     [!code-csharp[SP_SPDWFImport#2](../sharepoint/codesnippet/CSharp/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.cs#2)]
     [!code-vb[SP_SPDWFImport#2](../sharepoint/codesnippet/VisualBasic/workflowimportproject1/workflows/spd_task_workflowft/spd task workflow.xoml.vb#2)]

## <a name="deploy-the-project-and-associate-the-workflow"></a>프로젝트를 배포 하 고 워크플로 연결
 다음으로, WorkflowImportProject1 실행 SharePoint 사이트에 배포 하 고 다음 작업 목록 보기 및 수정 된 테스트를 사용 하 여 워크플로 연결 하려면 변환 워크플로.

#### <a name="to-deploy-the-project-and-associate-the-workflow"></a>프로젝트를 배포 하 고 워크플로 연결 하려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 선택 합니다 **F5** 실행 하 고 변환 된 워크플로 프로젝트를 배포 하는 키입니다.

2. 빠른 실행 모음에서 선택 합니다 **작업** 링크 작업 목록을 표시 합니다.

3. 에 **목록 도구** 탭을 선택 합니다 **항목** 단추를 선택한 후는 **새 항목** 단추입니다.

     합니다 **작업-새 항목** 대화 상자가 열립니다.

4. 에 **제목** 상자에 입력 합니다 **새 작업**를 선택한 후는 **저장** 단추입니다.

5. 에 **목록 도구** 탭을 선택 합니다 **목록** 단추를 선택한 후는 **목록 설정** 단추입니다.

     합니다 **목록 설정** 페이지가 나타납니다.

6. 에 **사용 권한 및 관리** 섹션을 선택 합니다 **워크플로 설정을** 링크 합니다.

     합니다 **워크플로 설정** 페이지가 나타납니다.

7. 선택 된 **워크플로 추가** 링크 합니다.

8. 에 **워크플로** 목록에서 선택 **WorkflowImportProject1-SPD Workflow Test**합니다.

9. 에 **이름** 상자에 입력 합니다 **SPD Workflow Test**를 선택한 후는 **확인** 단추입니다.

10. 빠른 실행 모음에서 선택 합니다 **작업** 목록입니다.

11. 옆의 화살표를 선택 **새 작업**을 선택한 후 목록에서 **워크플로**합니다.

12. **새 워크플로 시작** 섹션에 대 한 링크를 선택 합니다 **SPD Workflow Test**를 선택한 후는 **시작** 워크플로 시작 하는 단추.

    > [!NOTE]
    > 또는 하면 자동으로 연결할 수 워크플로 목록 사용 하 여 워크플로 설정 마법사를 실행 하 고 자동 연결 하는 워크플로 설정 합니다.

     두 작업 워크플로에 의해 수행 됩니다: 작업의 이름이 표시 **담당자** 열 및 공지 나타나는 합니다 **공지** 목록.

## <a name="see-also"></a>참고자료
- [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [웹 파트 또는 응용 프로그램 페이지에 대 한 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
