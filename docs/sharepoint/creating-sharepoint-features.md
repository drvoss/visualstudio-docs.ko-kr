---
title: SharePoint 기능 만들기 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, features
- features [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d3f453770dbb389a688db0a9edcc8e97e179858
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952748"
---
# <a name="create-sharepoint-features"></a>SharePoint 기능 만들기
  손쉬운 배포에 대 한 관련된 SharePoint 프로젝트 항목을 그룹화 하는 SharePoint 기능을 사용할 수 있습니다. 기능 만들기 하 고, 범위를 설정 하 고, SharePoint 기능 디자이너를 사용 하 여 다른 기능 종속성으로 표시할 수 있습니다. 디자이너에는 또한 각 기능을 설명 하는 XML 파일인 매니페스트를 생성 합니다.

## <a name="add-features-to-the-sharepoint-solution"></a>SharePoint 솔루션에 기능 추가
 솔루션 탐색기 또는 패키징 탐색기를 사용 하 여 SharePoint 솔루션에 기능을 추가할 수 있습니다. 기능을 추가 하려면 다음 방법 중 하나를 사용할 수 있습니다.

- **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 **기능**를 선택한 후 **기능 추가**합니다.

- **패키징 탐색기**, 패키지에 대 한 바로 가기 메뉴를 열고 선택한 후 **추가 기능**합니다.

## <a name="using-the-feature-designer"></a>기능 디자이너를 사용 하 여
 SharePoint 솔루션에는 솔루션 탐색기의 기능 노드 아래에 그룹화 되는 하나 이상의 SharePoint 기능을 포함할 수 있습니다. 각 기능에는 자체 **기능 디자이너** 기능 속성을 사용자 지정에 사용할 수 있습니다. 자세한 내용은 [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)합니다. 기능을 서로 구분 하려면 제목, 설명, 버전, 범위 등의 기능 속성을 구성할 수 있습니다.

### <a name="feature-designer-options"></a>기능 디자이너 옵션
 기능을 만든 후에 맞게 기능 디자이너를 사용할 수 있습니다.

 다음 표에서 기능 디자이너에 표시 되는 기능 속성을 설명 합니다.

|속성|설명|
|--------------|-----------------|
|제목|선택 사항입니다. 기능의 기본 제목으로 설정 되어 *SolutionName* *FeatureName*합니다.|
|설명|선택 사항입니다. SharePoint 기능의 설명입니다.|
|범위|필수 요소. 기능을 사용 하 여 만들어지면 **솔루션 탐색기**, 범위는 웹에 기본적으로 설정 됩니다.<br /><br /> -팜: 전체 서버 팜에 대 한 기능을 활성화 합니다.<br /><br /> -사이트: 사이트 컬렉션에 있는 모든 웹 사이트에 대 한 기능을 활성화 합니다.<br /><br /> -웹: 특정 웹 사이트에 대 한 기능을 활성화 합니다.<br /><br /> -웹 응용 프로그램: 웹 응용 프로그램에서 모든 웹 사이트에 대 한 기능을 활성화 합니다.|
|솔루션의 항목|기능에 추가할 수 있는 모든 SharePoint 항목입니다.|
|항목 기능|기능에 추가 된 SharePoint 프로젝트 항목입니다.|

## <a name="add-and-remove-sharepoint-project-items"></a>SharePoint 프로젝트 항목 추가 및 제거
 배포에 대 한 SharePoint 기능을 추가할 SharePoint 프로젝트 항목을 선택할 수 있습니다. 사용 된 **기능 디자이너** 추가 기능에 항목을 제거 하 고 기능 매니페스트를 확인 하려면. 자세한 내용은 [방법: SharePoint 기능에 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)합니다.

## <a name="add-feature-dependencies"></a>기능 종속성 추가
 SharePoint 서버 기능이 활성화 되기 전에 특정 기능을 활성화 하는 기능 매니페스트를 구성할 수 있습니다. 예를 들어, SharePoint 기능 기능이 나 데이터에 대 한 기타 기능에 의존 하는 경우 SharePoint 서버 기능에 의존 하는 기능을 활성화 하려면 먼저 수 있습니다. 자세한 내용은 [방법: 기능 종속성 추가 및 제거](../sharepoint/how-to-add-and-remove-feature-dependencies.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: SharePoint 기능 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-feature.md)
- [방법: SharePoint 기능에 항목 추가 및 제거](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)
- [방법: 기능 종속성 추가 및 제거](../sharepoint/how-to-add-and-remove-feature-dependencies.md)
