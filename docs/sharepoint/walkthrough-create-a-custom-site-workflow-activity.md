---
title: '연습: 사용자 지정 사이트 워크플로 작업 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, custom workflow activities
- site workflows [SharePoint development in Visual Studio]
- workflow activities [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, site workflows
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f717345689de9be640e03e9c7d81726a57d494b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008361"
---
# <a name="walkthrough-create-a-custom-site-workflow-activity"></a>연습: 사용자 지정 사이트 워크플로 작업 만들기
  이 연습에 사용 하 여 사이트 수준 워크플로에 사용자 지정 활동을 만드는 방법을 보여 줍니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. (사이트 수준 워크플로 사이트에서 목록 뿐 아니라 전체 사이트에 적용 합니다.) 사용자 지정 활동 알림 목록을 백업을 만들고 알림 목록의 내용을 그 안에 복사 합니다.

 이 연습에서는 다음 작업을 수행합니다.

- 사이트 수준 워크플로 만드는 중입니다.

- 사용자 지정 워크플로 활동을 만드는 중입니다.

- 만들고 SharePoint 목록을 삭제 합니다.

- 다른 하나의 목록에서 항목을 복사 합니다.

- 빠른 실행 모음에서 목록을 표시 합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 및 SharePoint입니다.

- Visual Studio.

## <a name="create-a-site-workflow-custom-activity-project"></a>사이트 워크플로 사용자 지정 활동 프로젝트 만들기
 먼저 프로젝트를 보관 하 고 테스트 사용자 지정 워크플로 작업을 만듭니다.

#### <a name="to-create-a-site-workflow-custom-activity-project"></a>사이트 워크플로 사용자 지정 활동 프로젝트를 만들려면

1. 메뉴 모음에서 선택 **파일** > **새로 만들기** > **프로젝트** 표시 하는 **새 프로젝트** 대화 상자.

2. 확장 합니다 **SharePoint** 노드 아래 **Visual C#** 또는 **Visual Basic**를 선택한 후는 **2010** 노드.

3. 에 **템플릿을** 창 선택 합니다 **SharePoint 2010 프로젝트** 템플릿.

4. 에 **이름** 상자에 입력 합니다 **AnnouncementBackup**를 선택한 후는 **확인** 단추입니다.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

5. 에 **디버깅에 대 한 사이트 및 보안 수준을 지정** 페이지를 선택 합니다 **팜 솔루션으로 배포** 옵션 단추를 선택한 후는 **마침** 단추를를 신뢰 수준 및 기본 사이트입니다.

     이 단계는 팜 솔루션에 워크플로 프로젝트에만 사용할 수 있는 옵션으로 솔루션의 신뢰 수준을 설정합니다.

6. **솔루션 탐색기**, 프로젝트 노드를 선택한 다음, 메뉴 모음에서 **프로젝트** > **새 항목 추가**합니다.

7. 준 **Visual C#** 또는 **Visual Basic**를 확장 합니다 **SharePoint** 노드를 선택한 후는 **2010** 노드.

8. 에 **템플릿** 창 선택 합니다 **순차 워크플로 (팜 솔루션에만 해당)** 템플릿을 선택한 후는 **추가** 단추.

     합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

9. 에 **디버깅을 위한 워크플로 이름을** 페이지에서 기본 이름을 (AnnouncementBackup-Workflow1). 에 워크플로 템플릿 형식을 변경 **사이트 워크플로**를 선택한 후 합니다 **다음** 단추입니다.

10. 선택 된 **완료** 단추 나머지 기본 설정을 적용 합니다.

## <a name="add-a-custom-workflow-activity-class"></a>사용자 지정 워크플로 활동 클래스를 추가 합니다.
 다음으로, 사용자 지정 워크플로 활동에 대 한 코드를 포함 하는 프로젝트에 클래스를 추가 합니다.

#### <a name="to-add-a-custom-workflow-activity-class"></a>사용자 지정 워크플로 활동 클래스를 추가 하려면

1. 메뉴 모음에서 선택 **프로젝트** > **새 항목 추가** 표시 하는 **새 항목 추가** 대화 상자.

2. **설치 된 템플릿** 트리 뷰를 선택 합니다 **코드** 노드를 선택한 후는 **클래스** 템플릿 프로젝트 항목 템플릿 목록에서. 기본 이름을 Class1를 사용 합니다. **추가** 단추를 선택합니다.

3. 다음을 사용 하 여 모든 Class1의 코드를 대체 합니다.

     [!code-csharp[SP_AnnBackup#1](../sharepoint/codesnippet/CSharp/announcementbackup/class1.cs#1)]
     [!code-vb[SP_AnnBackup#1](../sharepoint/codesnippet/VisualBasic/announcementbackupvb/class1.vb#1)]

4. 프로젝트를 저장 한 다음 메뉴 모음에서 선택 **빌드합니다** > **솔루션 빌드**합니다.

     Class1에서 사용자 지정 작업으로 표시 됩니다는 **도구 상자** 에 **AnnouncementBackup 구성 요소** 탭 합니다.

## <a name="add-the-custom-activity-to-the-site-workflow"></a>사이트 워크플로에 사용자 지정 활동을 추가 합니다.
 다음으로, 사용자 지정 코드를 포함 하는 워크플로 활동을 추가 합니다.

#### <a name="to-add-a-custom-activity-to-the-site-workflow"></a>사이트 워크플로에 사용자 지정 활동을 추가 하려면

1. Workflow1 디자인 보기에서 워크플로 디자이너에서 엽니다.

2. Class1 끌어 합니다 **도구 상자** 아래에 나타나는 `onWorkflowActivated1` 활동 또는 Class1에 대 한 바로 가기 메뉴를 열고 선택 **복사**, 아래의 줄에 대 한 바로 가기 메뉴를 열고는 `onWorkflowActivated1` 활동을 선택한 후 **붙여넣기**합니다.

3. 프로젝트를 저장합니다.

## <a name="test-the-site-workflow-custom-activity"></a>사용자 지정 사이트 워크플로 작업 테스트
 다음으로 프로젝트를 실행 하 고 사이트 워크플로 시작 합니다. 사용자 지정 활동 백업 알림 목록을 만들고이를 현재 알림 목록에서 내용을 복사 합니다. 또한 코드는 백업 목록을 새로 만들기 전에 이미 있는지 여부를 확인 합니다. 백업 목록에 이미 있으면 삭제 됩니다. 코드는 또한 SharePoint 사이트의 빠른 실행 모음에서 새 목록에 대 한 링크를 추가합니다.

#### <a name="to-test-the-site-workflow-custom-activity"></a>사이트 워크플로 사용자 지정 작업을 테스트 하려면

1. 선택 된 **F5** 프로젝트를 실행 하 여 SharePoint에 배포 하는 키입니다.

2. 빠른 실행 모음에서 선택 합니다 **나열** 모든 SharePoint 사이트에서 사용할 수 있는 목록을 표시 하는 링크입니다. 라는 알림 목록을 하나만 있는지 확인 **공지**합니다.

3. SharePoint 웹 페이지의 맨 위에 있는 선택 된 **사이트 워크플로** 링크 합니다.

4. 새 워크플로 섹션 시작을 선택 합니다 **AnnouncementBackup-Workflow1** 링크 합니다. 사이트 워크플로 시작 하 고 사용자 지정 작업에서 코드를 실행 합니다.

5. 빠른 실행 모음에서 선택 합니다 **공지 백업** 링크 합니다. 모든에 포함 된 알림이 **공지** 새 목록에 복사 된 목록.

## <a name="see-also"></a>참고자료
- [방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
