---
title: '연습: 기능 이벤트 수신자 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, advanced packaging tools
- SharePoint development in Visual Studio, event receivers
- SharePoint development in Visual Studio, feature event receivers
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0fc22e0c8ae0b0bdaf0729b3cdb3847cd25f580f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008288"
---
# <a name="walkthrough-add-feature-event-receivers"></a>연습: 기능 이벤트 수신자 추가
  기능 이벤트 수신기는 SharePoint의 다음 기능 관련 이벤트 중 하나가 발생할 때 실행 하는 메서드:

- 기능 설치 됩니다.

- 기능을 활성화 합니다.

- 기능이 비활성화 됩니다.

- 기능 제거 됩니다.

  이 연습에는 SharePoint 프로젝트의 기능 이벤트 수신기를 추가 하는 방법을 보여 줍니다. 다음 작업을 보여 줍니다.

- 기능 이벤트 수신기를 사용 하 여 빈 프로젝트를 만드는 중입니다.

- 처리를 **FeatureDeactivating** 메서드.

- 공지 알림 목록에 추가할 SharePoint 프로젝트 개체 모델을 사용 합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- 지원되는 Microsoft Windows 및 SharePoint 버전.

- Visual Studio.

## <a name="create-a-feature-event-receiver-project"></a>기능 이벤트 수신기 만들기
 기능 이벤트 수신기를 포함 하도록 프로젝트를 먼저 만듭니다.

#### <a name="to-create-a-project-with-a-feature-event-receiver"></a>기능 이벤트 수신기를 사용 하 여 프로젝트를 만들려면

1. 메뉴 모음에서 선택 **파일** > **새로 만들기** > **프로젝트** 표시 하는 **새 프로젝트** 대화 상자.

2. 확장 합니다 **SharePoint** 노드 아래 **Visual C#** 또는 **Visual Basic**를 선택한 후는 **2010** 노드.

3. 에 **템플릿을** 창 선택 합니다 **SharePoint 2010 프로젝트** 템플릿.

     프로젝트 템플릿은 있기 때문에 기능 이벤트 수신자가 프로젝트 형식을 사용 합니다.

4. 에 **이름** 상자에 입력 합니다 **FeatureEvtTest**를 선택한 후는 **확인** 표시 하려면 단추를 **SharePoint 사용자 지정 마법사**.

5. 에 **디버깅에 대 한 사이트 및 보안 수준을 지정할** 페이지에서 새 사용자 지정 필드 항목을 추가 하려는 SharePoint 서버 사이트의 URL을 입력 하거나 기본 위치를 사용 하 여 (http://\<*시스템 이름*> /).

6. 에 **이 SharePoint 솔루션의 신뢰 수준을?** 섹션을 선택 합니다 **팜 솔루션으로 배포** 옵션 단추입니다.

     샌드박스 솔루션과 팜 솔루션 비교에 대 한 자세한 내용은 참조 하세요. [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)합니다.

7. 선택 합니다 **완료** 단추를 클릭 한 다음 Feature1 이라고 하는 기능 아래에 표시 되는지 확인 합니다 **기능** 노드.

## <a name="add-an-event-receiver-to-the-feature"></a>기능 이벤트 수신기를 추가 합니다.
 다음으로, 기능 이벤트 수신기를 추가 하 고 기능이 비활성화 될 때 실행 되는 코드를 추가 합니다.

#### <a name="to-add-an-event-receiver-to-the-feature"></a>기능 이벤트 수신기를 추가 하려면

1. 기능 노드의 바로 가기 메뉴를 열고 선택한 **기능 추가** 기능을 만드는 합니다.

2. 아래는 **기능** 노드를 바로 가기 메뉴를 열고 **Feature1**를 선택한 후 **이벤트 수신기 추가** 기능 이벤트 수신기를 추가 하 합니다.

     이 Feature1에서 코드 파일을 추가합니다. 이 예에서 것 이라는 이름의 *Feature1.EventReceiver.cs* 또는 *Feature1.EventReceiver.vb*프로젝트의 개발 언어에 따라 합니다.

3. 프로젝트 작성 된 경우 [!INCLUDE[csprcs](../sharepoint/includes/csprcs-md.md)], 아직 없는 경우 이벤트 수신기의 맨 위에 있는 다음 코드를 추가 합니다.

     [!code-csharp[SP_FeatureEvt#1](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#1)]

4. 이벤트 수신기 클래스는 이벤트로 작동 하는 여러 주석 처리 된 메서드를 포함 합니다. 대체는 **FeatureDeactivating** 메서드를 다음:

     [!code-vb[SP_FeatureEvt#2](../sharepoint/codesnippet/VisualBasic/featureevt2vb/features/feature1/feature1.eventreceiver.vb#2)]
     [!code-csharp[SP_FeatureEvt#2](../sharepoint/codesnippet/CSharp/featureevttest2/features/feature1/feature1.eventreceiver.cs#2)]

## <a name="test-the-feature-event-receiver"></a>기능 이벤트 수신기를 테스트 합니다.
 다음으로 테스트 하는 기능을 비활성화 하는지 여부를 **FeatureDeactivating** 메서드 SharePoint 알림 목록에 공지를 출력 합니다.

#### <a name="to-test-the-feature-event-receiver"></a>기능 이벤트 수신기를 테스트 하려면

1. 프로젝트의 값을 설정 **활성 배포 구성을** 속성을 **활성화 없음**합니다.

     이 속성을 설정 기능을 SharePoint에서 활성화 방지 및 기능 이벤트 수신기를 디버깅할 수 있습니다. 자세한 내용은 [디버그 SharePoint 솔루션](../sharepoint/debugging-sharepoint-solutions.md)합니다.

2. 선택 된 **F5** 프로젝트를 실행 하 여 SharePoint에 배포 하는 키입니다.

3. SharePoint 웹 페이지의 맨 위에 있는 열을 **사이트 작업** 메뉴를 선택한 후 **사이트 설정**합니다.

4. 아래는 **사이트 작업** 섹션을 **사이트 설정** 페이지를 선택 합니다 **사이트 기능 관리** 링크.

5. 에 **기능** 페이지를 선택 합니다 **활성화** 단추 옆에 **FeatureEvtTest Feature1** 기능입니다.

6. 에 **기능** 페이지를 선택 합니다 **비활성화** 단추 옆에 **FeatureEvtTest Feature1** 기능을 선택한 후는 **이 기능을 비활성화**  확인 링크 기능을 비활성화 합니다.

7. 선택 된 **홈** 단추입니다.

     에 알림이 표시 하는 **공지** 기능이 비활성화 되 면 목록.

## <a name="see-also"></a>참고자료

- [방법: 이벤트 수신기 만들기](../sharepoint/how-to-create-an-event-receiver.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)