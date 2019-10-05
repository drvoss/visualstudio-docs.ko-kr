---
title: '방법: 리소스 파일 추가 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- resource files [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, resource files
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7b8394d0c21ed5a45639e4dad5fe3695aaccc27
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439998"
---
# <a name="how-to-add-a-resource-file"></a>방법: 리소스 파일 추가
  리소스 파일을 추가 하기 위한 명령을 솔루션 노드와 솔루션 탐색기에서 기능 노드의 바로 가기 메뉴를 켜져 있습니다. 자세한 내용은 [지역화 SharePoint 솔루션](../sharepoint/localizing-sharepoint-solutions.md)합니다.

### <a name="to-add-a-global-resource-file-to-a-sharepoint-solution"></a>SharePoint 솔루션에 전역 리소스 파일을 추가 하려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], SharePoint 솔루션을 엽니다.

2. **솔루션 탐색기**, SharePoint 프로젝트 노드를 선택한 다음, 메뉴 모음에서 **프로젝트** > **새 항목 추가**합니다.

3. 에 **새 항목 추가** 대화 상자를 선택 합니다 **전역 리소스 파일** 템플릿을 선택한 후는 **추가** 단추.

   > [!NOTE]
   > 전역 리소스 파일 프로젝트 항목 템플릿을 SharePoint 프로젝트 항목을 선택한 경우에 나타납니다.

4. 에 **리소스 추가** 대화 상자에서 문화권을 영어 (미국)와 같은 리소스 파일을 선택 합니다.

    이 단계에서는 Resource_x_ 형식으로 솔루션에 전역 리소스 파일을 추가 **.** <em>문화권</em><strong>.</strong> resx와 같은 *Resource1.en US.resx*합니다.

5. 경우는 **리소스 편집기** 열립니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 리소스 파일에 리소스를 추가 합니다.

### <a name="to-add-a-feature-resource-file-to-a-sharepoint-feature"></a>SharePoint 기능을 기능 리소스 파일을 추가 하려면

1. SharePoint 솔루션을 이미에서 열려 있지 않으면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 솔루션을 엽니다.

2. **솔루션 탐색기**, 아래에 있는 기능의 이름에 대 한 바로 가기 메뉴를 열고 합니다 **기능** 노드를 선택한 후 **기능 리소스 추가**합니다.

     이 단계에서는 형식에서 기능 리소스 파일을 추가 _ResourceFileName_**.** _문화권_**.resx**와 같은 *Feature1.en US.resx*합니다.

3. 경우는 **리소스 편집기** 열립니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 리소스 파일에 리소스를 추가 합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
