---
title: SharePoint 워크플로 솔루션 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VSTO.NewSharePointWorkflowWizard.Page3
- VS.SharePointTools.Workflow.WorkflowName
- VSTO.NewSharePointWorkflowWizard.Page2
- VSTO.NewSharePointWorkflowWizard.Page1
dev_langs:
- VB
- CSharp
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
ms.openlocfilehash: d78d82a51f88bfaf076b56692629e801689e103e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443534"
---
# <a name="create-sharepoint-workflow-solutions"></a>SharePoint 워크플로 솔루션 만들기

[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 문서 및 SharePoint 웹 사이트에서 목록 항목의 수명 주기를 관리 하는 사용자 지정 워크플로 만들 수 있도록 도구를 제공 합니다. 제공되는 항목에는 디자이너, 작업 컨트롤 집합 및 필수 어셈블리 참조가 있습니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 또한 합니다 **SharePoint 사용자 지정 마법사**, 만들기 및 워크플로 구성 하는 데 합니다.

SharePoint에 대 한 자세한 내용은 참조 하세요. [Microsoft SharePoint 제품 및 기술](http://go.microsoft.com/fwlink/?LinkId=178470)합니다.

## <a name="workflows-in-sharepoint"></a>SharePoint에서 워크플로
 워크플로 SharePoint 라이브러리 또는 목록에 추가 하면 라이브러리 또는 목록에 있는 모든 항목에서 비즈니스 프로세스를 적용 합니다. 워크플로는 시스템 또는 사용자를 편집 하 고 검토 한 다음 항목을 보내는 등의 각 항목에 대해 수행 해야 하는 작업을 설명 합니다. 라고 하는 이러한 작업을 *활동*은 워크플로의 구성 요소입니다.

 SharePoint 워크플로 만들 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 하 고 SharePoint 웹 사이트에 배포 합니다. 워크플로 SharePoint에 배포 된 후 목록 또는 라이브러리를 사용 하 여 연결 합니다. 그런 다음 시작 자동으로 프로세스에 의해 또는 사용자가 수동으로. 워크플로 작업에 대 한 자세한 내용은 참조 하세요. [Visual Studio를 사용 하 여 SharePoint 개발 워크플로](https://docs.microsoft.com/sharepoint/dev/general-development/develop-sharepoint-workflows-using-visual-studio)합니다.

## <a name="create-custom-sharepoint-workflows"></a>사용자 지정 SharePoint 워크플로 만들기
 두 SharePoint 워크플로 프로젝트에서 사용할 수 있는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]: **순차 워크플로** 하 고 **상태 시스템 워크플로**합니다.

 A *순차 워크플로* 일련의 단계를 나타냅니다. 마지막 작업이 완료 될 때까지 단계를 하나씩 수행 됩니다. 순차 워크플로 항상 반드시 순서 대로 실행 합니다. 외부 이벤트를 수신 하 고 병렬 논리 흐름을 포함할 수 있습니다, 실행의 정확한 순서는 달라질 수 있습니다. 다음 그림에서는 순차 워크플로의 예를 보여 줍니다.

 ![순차 워크플로](../sharepoint/media/sp-sequential.png "순차 워크플로")

 A *상태 시스템 워크플로* 상태, 전환 및 동작의 집합을 나타냅니다. 상태 시스템 워크플로의 단계를 비동기적으로 실행 합니다. 즉, 이러한 휴대폰이 반드시 수행 되지 않습니다 하지만 대신 작업 및 상태에 의해 트리거되는 합니다. 이상의 상태가 시작 상태로 할당 됩니다 및 그런 다음 이벤트에 따라는 다른 상태로 전환 합니다. 상태 시스템 워크플로의 끝을 결정 하는 최종 상태에 있을 수 있습니다. 다음 다이어그램은 상태 시스템 워크플로의 예를 보여 줍니다.

 ![상태 시스템 워크플로](../sharepoint/media/sp-state.png "상태 시스템 워크플로")

 워크플로 유형에 대 한 자세한 내용은 참조 하세요. [워크플로 유형](http://go.microsoft.com/fwlink/?LinkId=178995)합니다.

### <a name="use-the-wizard"></a>마법사를 사용 합니다.
 SharePoint 워크플로 프로젝트를 만들면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 먼저에서 해당 설정을 지정 합니다 **SharePoint 사용자 지정 마법사**합니다. 마법사는 이러한 설정을 사용 하 여 프로젝트를 만듭니다 **솔루션 탐색기**합니다. 이 프로젝트는 코드 파일, 워크플로 배포 하는 데 사용 되는 여러 파일을 포함 하 고 사용자 지정 SharePoint 워크플로 만드는 데 필요한 어셈블리를 참조 합니다.

 워크플로 만든 후 속성 창에서 해당 속성을 수정할 수 있습니다. 대부분의 워크플로 속성이 속성 창에서 직접 변경할 수 있지만 일부 해야 줄임표 단추를 클릭 (![ASP.NET 모바일 디자이너 줄임표](../sharepoint/media/mwellipsis.gif "ASP.NET 모바일 디자이너 줄임표"))를 해당 값을 변경 합니다. 이 단추를 다시 시작 합니다 **SharePoint 사용자 지정 마법사**합니다. 선택 값이 변경 된 속성을 변경한 후 합니다 **완료** 단추 하 여 종료 합니다.

> [!NOTE]
> 합니다 **워크플로 유형** 속성이 읽기 전용 이므로 변경할 수 없습니다. 워크플로 형식을 변경 하려는 경우에 다른 워크플로 만들어야 합니다.

## <a name="design-a-sharepoint-workflow"></a>SharePoint 워크플로 디자인 합니다.
 사용 하 여 비즈니스 프로세스에서 모든 단계를 정의 하 고 나면는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 워크플로 디자이너는 SharePoint 워크플로 디자인 합니다. 디자이너를 열려면에서 Workflow1.cs 또는 Workflow1.vb를 두 번 클릭 **솔루션 탐색기**, 또는 이러한 파일 중 하나에 대 한 바로 가기 메뉴를 열고 선택한 후 **엽니다**합니다.

### <a name="activities"></a>활동
 워크플로 디자인 하려면 활동을 추가 합니다 **도구 상자** 에 *워크플로 일정* 디자이너에서 합니다. 워크플로 일정 순서 대로 수행 해야 하는 작업 시퀀스를 포함 합니다.

 활동의는 다음과 같은 두 종류가 있습니다.

- *간단한 작업* "1 일에 대 한 지연" 또는 "웹 서비스를 시작 합니다."와 같은 작업의 단일 단위를 수행 합니다.

- *복합 활동* 다른 활동을 포함할; 예를 들어 조건부 작업을 두 개의 분기가 포함 합니다.

  두 종류의 작업에 사용할 수는 **도구 상자**합니다.

  작업 속성, 메서드 및 이벤트에 있을 수 있습니다. 사용 된 **속성** 활동의 속성을 설정 하는 창입니다.

  또한 사용자 지정 활동을 만들 수 있습니다. 자세한 내용은 [연습: 사용자 지정 사이트 워크플로 활동을 만드는](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)합니다.

  작업에서 다음 탭에서 구성 합니다 **도구 상자**:

- **SharePoint 워크플로**

- **Windows Workflow v3.0**

- **Windows Workflow v3.5**

  모든 핵심 워크플로 작업은 SharePoint에서 지원 됩니다. 자세한 내용은 [워크플로 활동에 대 한 Windows SharePoint Services 개요](http://go.microsoft.com/fwlink/?LinkID=156094)합니다.

#### <a name="sharepoint-workflow-activities"></a>SharePoint 워크플로 활동이
 합니다 **SharePoint 워크플로** 탭에서 사용 하기 위해 특수 한 활동을 포함할 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]합니다. 이러한 작업은 간단 하 고 문서 수명 주기 워크플로 개발을 간소화 합니다. 에 표시 되는 작업에 대 한 자세한 내용은 합니다 **SharePoint 워크플로** 탭을 참조 하십시오 [워크플로 활동에 대 한 Windows SharePoint Services 개요](http://go.microsoft.com/fwlink/?LinkID=156094)합니다.

#### <a name="windows-workflow-activities"></a>Windows 워크플로 작업
 합니다 **Windows Workflow** 탭에서 제공 하는 작업을 포함 합니다 [!INCLUDE[TLA#tla_workflow](../sharepoint/includes/tlasharptla-workflow-md.md)]합니다. 모든 종류의 Windows 워크플로 응용 프로그램에 대 한 워크플로 일정을 만들려면 이러한 활동을 사용할 수 있습니다.

 에 표시 되는 작업에 대 한 자세한 내용은 합니다 **Windows 워크플로** 탭을 참조 하십시오 [Windows Workflow Foundation 활동](http://go.microsoft.com/fwlink/?LinkID=156096)합니다. Windows Workflow Foundation에 대 한 자세한 내용은 참조 하세요. [Windows Workflow Foundation 개요](http://go.microsoft.com/fwlink/?LinkID=128632)합니다.

### <a name="work-with-activities-in-the-designer"></a>디자이너에서 작업을
 워크플로 일정 Windows 워크플로 활동 및 SharePoint 워크플로 활동의 조합을 포함할 수 있습니다.

 디자이너를 배치 하 고 작업을 올바르게 구성 하는 데 시각 신호를 표시 합니다. 작업을 워크플로 일정으로 끌거나 복사하면 워크플로에서 해당 작업의 올바른 위치를 보여 주는 녹색 더하기 기호(+) 아이콘이 디자이너에 표시됩니다. 유효한 없게 없는 위치에 활동을 배치할 수 없습니다. 예를 들어 수신 작업 분기의 첫 번째 활동으로 송신 작업을 이동할 수 없습니다. 자세한 내용은 [SharePoint Designer 개발자 센터](http://go.microsoft.com/fwlink/?LinkId=178476)합니다.

## <a name="collect-information-during-the-workflow"></a>워크플로 중에 정보를 수집 합니다.
 사용자 로부터 정보를 수집 하는 것이 좋습니다에 미리 정의 된 워크플로에서 시간입니다. 양식 또는 항목 속성을 사용 하 여 정보를 수집할 수 있습니다.

### <a name="forms"></a>양식
 Forms 질문을 포함 하 고 사용자가 답변을 제공 하는 방법을 제공 하는 대화 상자와 같습니다.

 워크플로에서 사용할 수 있는 폼의는 방법은 네 가지가 있습니다.

- 연결

- 시작

- 수정

- 작업

  이러한 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 연결 및 초기화 폼에 대 한 항목 템플릿이 포함 되어 있습니다. 예는 *연결 양식* 지출 비용 워크플로의 등 워크플로에 관련 된 매개 변수를 워크플로 설치 관리자가 있는 입력 됩니다. 예는 *양식을* 은 입력을 소비 하는 워크플로에 비용 워크플로의 사용자 수입니다. 이러한 양식 유형에 대 한 자세한 내용은 참조 하세요. [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)합니다.

### <a name="item-properties"></a>항목 속성
 SharePoint 라이브러리 또는 목록 항목의 속성을 사용 하 여 사용자 로부터 정보를 수집할 수 있습니다. Workflow1.cs 또는 Workflow1.vb 주 코드 파일 이름의 Microsoft.SharePoint.Workflow.SPWorkflowActivationProperties.WorkflowProperties 클래스의 인스턴스를 선언 `workflowProperties`합니다. 사용 된 `workflowProperties` 라이브러리의 코드 목록 속성에 액세스 하는 개체입니다. 예제를 보려면 [연습: SharePoint 워크플로 솔루션을 만들고](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)합니다.

## <a name="debug-a-sharepoint-workflow-template"></a>SharePoint 워크플로 템플릿 디버그
 디버깅할 수 SharePoint 워크플로 프로젝트를 동일한 다른 디버그할 때 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 웹 기반 프로젝트입니다. 시작 하는 경우는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디버거를 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에 지정 된 설정을 사용 하는 **SharePoint 사용자 지정 마법사** 적절 한 SharePoint 웹 사이트를 열고 자동 워크플로 템플릿을 연결 적절 한 라이브러리 또는 목록입니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 또한 연결 합니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디버거를 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 라는 프로세스가 *w3wp.exe*합니다.

 워크플로 테스트 하려면이 수동으로 시작 해야 합니다. 자세한 내용은 "워크플로에 디버깅" 섹션을 참조 [SharePoint 솔루션 디버깅](../sharepoint/debugging-sharepoint-solutions.md)합니다. 에 대 한 자세한 내용은 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 웹 응용 프로그램 디버깅을 참조 하십시오 [웹 응용 프로그램 및 스크립트 디버그](../debugger/how-to-enable-debugging-for-aspnet-applications.md)합니다.

## <a name="deploy-a-sharepoint-workflow-template"></a>SharePoint 워크플로 템플릿 배포
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 워크플로 프로젝트 같은 다른 배포 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 프로젝트입니다. 자세한 내용은 [패키지 및 배포 하는 SharePoint 솔루션](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)합니다.

## <a name="import-globally-reusable-workflows"></a>전역적으로 재사용 가능한 워크플로 가져오기
 사이트별 재사용 가능한 워크플로 생성할 뿐만 아니라 SharePoint Designer 만들 수 있게 *전역적으로 재사용 가능한 워크플로*, 모든 SharePoint 사이트에서 사용할 수 있는 워크플로 합니다. 재사용 가능한 워크플로 가져오기 프로젝트 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 현재 전역적으로 재사용 가능한 워크플로 가져오지 않습니다. 그러나 SharePoint Designer를 사용 하 여 전역적으로 다시 사용할 수 있는 워크플로 다시 사용할 수 있는 워크플로로 변환할 하거나 변환 되지 않은 선언적 워크플로로 워크플로 가져옵니다. 자세한 내용은 [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)합니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[연습: 만들고 SharePoint 워크플로 솔루션을 디버그 합니다.](../sharepoint/walkthrough-creating-and-debugging-a-sharepoint-workflow-solution.md)|만들기 및 간단한 디버깅 과정을 단계별로 안내 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 워크플로.|
|[연습: 연결 및 초기화 폼을 사용 하 여 워크플로 만들기](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)|만들기는 더 완전 한 기능의을 단계별로 안내 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 연결 및 초기화 폼을 사용 하 여 워크플로 완료 합니다.|
|[연습: 워크플로에 응용 프로그램 페이지 추가](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)|항목 기반 [연습: 연결 및 초기화 폼을 사용 하 여 워크플로 만듭니다](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) 더 추가 하 여 *.aspx* 워크플로에 입력 한 데이터를 보고 하는 응용 프로그램 페이지입니다.|
|[연습: 사용자 지정 사이트 워크플로 작업 만들기](../sharepoint/walkthrough-create-a-custom-site-workflow-activity.md)|두 가지 주요 작업을 수행 하는 방법에 설명 합니다: 사이트 수준 워크플로 만들고 사용자 지정 워크플로 작업을 합니다.|
|[연습: Visual Studio에 SharePoint Designer의 재사용 가능한 워크플로 가져오기](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md)|SharePoint Designer 2010에서 만든 다시 사용할 수 있는 선언적 워크플로 가져오는 방법을 보여 줍니다는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 프로젝트입니다.|

## <a name="see-also"></a>참고자료

- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [SharePoint 용 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)