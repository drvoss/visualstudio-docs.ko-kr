---
title: '연습: 프로젝트 작업 목록 정의 배포 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7ea7063ce432841e812312b7c7c36721a7d2d099
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62784233"
---
# <a name="walkthrough-deploy-a-project-task-list-definition"></a>연습: 프로젝트 작업 목록 정의 배포

이 연습에서는 프로젝트 작업을 추적하기 위해 [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]를 사용하여 SharePoint 목록을 만들고, 사용자 지정하고, 디버깅하고, 배포하는 방법을 보여 줍니다.

[!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건

- 지원되는 Microsoft Windows 및 SharePoint 버전.

- Visual Studio 2017 또는 Azure DevOps 서비스입니다.

## <a name="create-a-sharepoint-list"></a>SharePoint 목록 만들기

SharePoint 목록 프로젝트를 만들고 목록 정의를 작업과 연결합니다.

1. 엽니다는 **새 프로젝트** 대화 상자에서 **SharePoint** 노드를 선택한 후는 **2010** 노드.

2. 에 **템플릿** 창 선택는 **SharePoint 2010 프로젝트** 서식 파일을 프로젝트의 이름 **ProjectTaskList**를 선택한 후는 **확인**단추입니다.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

3. 디버깅을 사용 하는 로컬 SharePoint 사이트를 지정 합니다. 선택 합니다 **팜 솔루션으로 배포** 옵션 단추를 선택한 후는 **완료** 단추입니다.

4. 프로젝트의 바로 가기 메뉴를 열고 선택한 **추가** > **새 항목**합니다.

5. 에 **템플릿** 창 선택 합니다 **목록** 템플릿을 선택한 후는 **추가** 단추.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

6. 에 **이름을 목록에 대해 표시 하 시겠습니까?** 상자에 입력 합니다 **프로젝트 작업 목록**합니다.

7. 선택 합니다 **의 기존 목록 형식을 기반으로 사용자 지정 가능한 비 목록을 만듭니다** 옵션 단추를 선택한 다음, 해당 목록에서 선택 **작업**를 선택한 후는 **마침** 단추.

     목록, 기능 및 패키지 나타나지 **솔루션 탐색기**합니다.

## <a name="add-an-event-receiver"></a>이벤트 수신기 추가

작업 목록에서 작업의 기한과 설명을 자동으로 설정하는 이벤트 수신기를 추가할 수 있습니다. 다음 절차는 이벤트 수신기로 목록 인스턴스에 간단한 이벤트 처리기를 추가합니다.

1. 프로젝트 노드에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 항목**합니다.

2. SharePoint 템플릿의 목록에서 선택 합니다 **이벤트 수신기** 서식 파일을 추가한 다음 이름을 **ProjectTaskListEventReceiver**합니다.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

3. 에 **이벤트 수신기 설정 선택** 페이지에서 **목록 항목 이벤트** 에서 이벤트 수신기 유형으로는 **이벤트 수신기 유형을 선택 하십시오** 목록입니다.

4. 에 **항목에 이벤트 소스가 있어야 합니다.** 목록에서 선택 **작업**합니다.

5. 처리할 이벤트 목록에서 선택 확인란 옆 **항목이 추가 되었습니다**를 선택한 후는 **마침** 단추.

     새 이벤트 수신기 노드 라는 코드 파일을 프로젝트에 추가 됩니다 **ProjectTaskListEventReceiver**합니다.

6. 코드를 추가 합니다 `ItemAdded` 의 메서드를 **ProjectTaskListEventReceiver** 코드 파일. 새 작업을 추가할 때마다 기한과 설명을 기본 작업에 추가 됩니다. 기본 기한은 날짜가 2009 년 7 월 1 일입니다.

     [!code-vb[SPProjectTaskList#1](../sharepoint/codesnippet/VisualBasic/projecttasklist1/projecttasklisteventreceiver/projecttasklisteventreceiver.vb#1)]
     [!code-csharp[SPProjectTaskList#1](../sharepoint/codesnippet/CSharp/projecttasklist/projecttasklisteventreceiver/projecttasklisteventreceiver.cs#1)]

## <a name="customize-the-project-task-list-feature"></a>프로젝트 작업 목록 기능을 사용자 지정

SharePoint 솔루션을 만들 때 Visual Studio 자동으로 기능을 만듭니다 기본 프로젝트 항목입니다. 기능 디자이너를 사용 하 여 SharePoint 사이트에 대 한 프로젝트 작업 목록 설정을 사용자 지정할 수 있습니다.

1. **솔루션 탐색기**를 확장 하 고 **기능**합니다.

2. 바로 가기 메뉴를 열고 **Feature1**를 선택한 후 **뷰 디자이너**합니다.

3. 에 **제목** 상자에 입력 합니다 **프로젝트 작업 목록 기능**합니다.

4. 에 **범위** 목록에서 선택 **웹**합니다.

5. 에 **속성** 창에서 입력 **1.0.0.0** 값으로는 **버전** 속성입니다.

## <a name="customize-the-project-task-list-package"></a>프로젝트 작업 목록 패키지를 사용자 지정

SharePoint 프로젝트를 만들면 Visual Studio는 자동으로 패키지를 기본 프로젝트 항목을 포함 하는 기능을 추가 합니다. 패키지 디자이너를 사용 하 여 SharePoint 사이트에 대 한 프로젝트 작업 목록 설정을 사용자 지정할 수 있습니다.

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 **패키지**를 선택한 후 **뷰 디자이너**합니다.

2. 에 **이름을** 상자에 입력 합니다 **ProjectTaskListPackage**합니다.

3. 선택 된 **웹 서버 다시 설정** 확인란 합니다.

## <a name="build-and-test-the-project-task-list"></a>빌드 및 테스트 프로젝트 작업 목록

프로젝트를 실행 하면 SharePoint 사이트가 열립니다. 그러나 작업 목록의 위치로 수동으로 이동 해야 있습니다.

1. 선택 된 **F5** 빌드 및 배포 프로젝트 작업 목록에는 키입니다.

     SharePoint 사이트가 열립니다.

2. 선택 된 **홈** 탭 합니다.

3. 왼쪽된 세로 막대를 선택 합니다 **프로젝트 작업 목록** 링크 합니다.

     프로젝트 작업 목록 페이지에 표시 됩니다.

4. 에 **목록 도구** 탭을 선택 합니다 **항목** 탭 합니다.

5. 에 **항목** 그룹에서 선택 합니다 **새 항목** 단추입니다.

6. 에 **제목** 텍스트 상자에 입력 합니다 **Task1**합니다.

7. 선택 된 **저장할** 단추입니다.

     사이트를 새로 고친 후 합니다 **Task1** 2009 년 7 월 1의 기한이 있는 작업이 표시 됩니다.

8. 선택할 **Task1**합니다.

     작업의 자세한 보기 나타나고 "중요 한 작업입니다."에 대 한 설명 표시

## <a name="deploy-the-project-task-list"></a>프로젝트 작업 목록 배포

를 빌드 및 프로젝트 작업 목록을 테스트 한 후 배포할 수 있습니다 하는 *로컬 시스템* 또는 *원격 시스템*입니다. 로컬 시스템 원격 시스템은 다른 컴퓨터 솔루션을 개발 하는 동일한 컴퓨터를입니다.

### <a name="to-deploy-the-project-task-list-to-the-local-system"></a>프로젝트 작업 목록을 로컬 시스템에 배포 하려면

Visual Studio 메뉴 모음에서 **빌드합니다** > **솔루션 배포**합니다.

Visual Studio 솔루션의 모든 기존 버전을 제거, 솔루션 패키지를 복사 합니다. IIS 응용 프로그램 풀 재활용 (*.wsp*) SharePoint에 파일 및 다음 기능을 활성화 합니다. 이제 SharePoint에서 솔루션을 사용할 수 있습니다. 배포 구성 단계에 대 한 자세한 내용은 참조 하세요. [방법: SharePoint 배포 구성 편집](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)합니다.

### <a name="to-deploy-the-project-task-list-to-a-remote-system"></a>프로젝트 작업 목록을 원격 시스템에 배포 하려면

1. Visual Studio 메뉴 모음에서 **빌드합니다** > **게시**합니다.

2. 에 **게시** 대화 상자를 선택 합니다 **파일 시스템에 게시** 옵션 단추입니다.

     대상 위치를 변경할 수 있습니다 합니다 **게시** 줄임표 단추를 선택 하 여 대화 상자 ![줄임표 아이콘](../sharepoint/media/ellipsisicon.gif "줄임표 아이콘") 다른 위치로 이동한 후 합니다.

3. 선택 된 **게시** 단추입니다.

     A *.wsp* 솔루션 파일이 생성 됩니다.

4. 복사 합니다 *.wsp* 원격 SharePoint 시스템에는 파일입니다.

5. PowerShell을 사용 하 여 `Add-SPUserSolution` 원격 SharePoint 설치 패키지를 설치 하는 명령입니다. (팜 솔루션에 대해 사용 된 `Add-SPSolution` 명령입니다.)

     예를 들어, `Add-SPUserSolution C:\MyProjects\ProjectTaskList\ProjectTaskList\bin\Debug\ProjectTaskList.wsp`을 입력합니다.

6. PowerShell을 사용 하 여 `Install-SPUserSolution` 솔루션을 배포 하는 명령입니다. (팜 솔루션에 대해 사용 된 `Install-SPSolution` 명령입니다.)

     예를 들어, `Install-SPUserSolution -Identity ProjectTaskList.wsp -Site http://NewSiteName`을 입력합니다.

     원격 배포에 대 한 자세한 내용은 참조 하세요. [를 사용 하 여 솔루션](http://go.microsoft.com/fwlink/?LinkId=217680) 하 고 [추가 하 고 SharePoint 2010에서 PowerShell 사용 하 여 솔루션 배포](http://go.microsoft.com/fwlink/?LinkId=217682)합니다.

## <a name="next-steps"></a>다음 단계

사용자 지정 하 고 다음 항목에서 SharePoint 솔루션을 배포 하는 방법에 알아볼 수 있습니다.

- [연습: SharePoint 용 사이트 열, 콘텐츠 형식 및 목록 만들기](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)

- [방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md)

- [SharePoint Server 2010 용 Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=217684)

## <a name="see-also"></a>참고자료
[패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
