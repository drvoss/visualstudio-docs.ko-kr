---
title: '방법: BDC 모델 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9126a0d3bb552f525247cbfb2243504a1effaa92
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435466"
---
# <a name="how-to-create-a-bdc-model"></a>방법: BDC 모델 만들기
  템플릿을 사용 하 여 해당 종류의 항목에 대 한 다음 SharePoint 프로젝트 모델을 추가 하 여 비즈니스 데이터 연결 (BDC) 모델을 만들 수 있습니다. 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)합니다. 모델을 디자인 하는 방법에 대 한 자세한 내용은 참조 하세요. [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)합니다.

### <a name="to-create-a-bdc-project"></a>BDC 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

    > [!NOTE]
    > IDE가 Visual Basic 개발 설정을 사용 하도록 설정 하는 경우 선택할 **파일** > **새 프로젝트**합니다.

     **새 프로젝트** 대화 상자가 열립니다.

2. 준 **Visual Basic** 또는 **Visual C#**, 선택 **Office/SharePoint**하십시오 **SharePoint 솔루션**.

3. 에 **템플릿** 창 선택 합니다 **SharePoint 2013-빈 프로젝트** 항목을 선택한 후는 **확인** 단추.

     합니다 **SharePoint 사용자 지정 마법사** 열립니다.

4. 에 **디버깅에 대 한 사이트 및 보안 수준을 지정** 페이지에서 로컬 컴퓨터의 SharePoint 사이트의 URL을 지정을 선택 합니다 **팜 솔루션으로 배포** 옵션 단추를 선택한 후는 **완료** 단추입니다.

     지정 된 SharePoint 사이트에서 모델을 테스트 합니다.

    > [!IMPORTANT]
    > BDC 모델은 팜 솔루션만 지원 하므로 팜 솔루션으로 프로젝트를 배포 해야 합니다.

     빈 SharePoint 프로젝트가 만들어집니다.

5. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

6. 에 **새 항목 추가** 대화 상자를 선택 합니다 **Office/SharePoint** 노드.

7. SharePoint 템플릿의 목록에서 선택 **비즈니스 데이터 연결 모델 (팜 솔루션만 해당)** 합니다.

8. 에 **이름** 상자, BDC 모델에 대 한 이름을 지정 하 고 선택한 합니다 **추가** 단추입니다.

     A **비즈니스 데이터 연결 모델** 항목이 프로젝트에 추가 됩니다. 기본적으로 모델 BDC 디자이너에 나타납니다. 자세한 내용은 [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)합니다.

## <a name="see-also"></a>참고자료
- [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)
- [방법: SharePoint 프로젝트에 기존 BDC 모델 파일 추가](../sharepoint/how-to-add-an-existing-bdc-model-file-to-a-sharepoint-project.md)
- [방법: 리소스 파일을 사용 하 여 지역화 된 이름, 속성 및 사용 권한을 지정 합니다.](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md)
- [방법: BDC 기능에 사용자 지정 어셈블리 포함](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md)
- [SharePoint에 비즈니스 데이터 통합](../sharepoint/integrating-business-data-into-sharepoint.md)
