---
title: '방법: 마스터 페이지 또는 테마 가져오기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, importing items
- importing items [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6cac959fb4f9c52849e6e121943fd847deb923d0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427395"
---
# <a name="how-to-import-a-master-page-or-theme"></a>방법: 마스터 페이지 또는 테마 가져오기
  제공할 수 있습니다 페이지 SharePoint 사이트에서 일관 된 모양을 만들고 마스터 페이지 및 테마를 사용 하 여. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 이러한 요소에 대 한 템플릿을 제공 하지 않습니다 SharePoint Designer에서 만들고를 다음으로 가져와야 하지만 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. 자세한 내용은 참조 하세요. [문서 블록: 페이지 및 사용자 인터페이스](http://go.microsoft.com/fwlink/?LinkID=182095) Microsoft 웹 사이트입니다.

### <a name="to-import-a-master-page-or-theme"></a>마스터 페이지 또는 테마 가져오기

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 만들거나 SharePoint 프로젝트를 엽니다.

     SharePoint 프로젝트를 만드는 방법에 대 한 자세한 내용은 [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)합니다.

2. 메뉴 모음에서 **프로젝트** > **새 항목 추가**를 선택합니다.

3. 에 **새 항목 추가** 대화 상자에서 합니다 **SharePoint** 노드를 선택한 후는 **2010** 노드.

4. SharePoint 템플릿의 목록에서 선택 합니다 **모듈** 템플릿을 모듈에 대 한 이름을 지정 합니다.

     모듈에는 SharePoint에서 지정 하는 위치에 배포에 대 한 파일 (예: 마스터 페이지 또는 테마 파일)를 포함 합니다.

5. 모듈의 이름으로 지정 된 기본 파일을 삭제할 *Sample.txt*합니다.

6. 모듈 노드를 선택 합니다.

7. 메뉴 모음에서 선택 **프로젝트** > **기존 항목 추가**, 고 마스터 페이지 또는 테마 파일을 선택 합니다.

     마스터 페이지 파일 확장명이.master 및 테마 파일 확장명이.thmx 합니다.

8. 마스터 페이지를 추가한 경우 변경 해당 **배포 충돌 해결** 설정을 **자동** 모듈의 속성입니다.

    > [!NOTE]
    > 마스터 페이지의 이름이 기본 마스터 페이지 또는 사용자 지정 마스터 페이지에 표시 된 기존 마스터 페이지의 이름과 같은 경우 오류가 발생할 수 있습니다. 이 문제를 해결 하는 방법에 대 한 정보를 참조 하세요. [연습: 사용자 지정 마스터 페이지 및 사이트 페이지를 이미지로 가져오기](../sharepoint/walkthrough-import-a-custom-master-page-and-site-page-with-an-image.md)합니다.

9. 모듈을 엽니다 *Elements.xml*합니다.

     업데이트 해야 합니다 *Elements.xml* 추가한 테마를 마스터 페이지를 참조 하는 파일입니다.

10. 마스터 페이지에 대 한 기존 모듈 태그를 다음 태그로 바꿉니다.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/masterpage">
        <File Path="[Module Name]\[Master Page Name].master"
          Url="[Master Page Name].master" Type="GhostableInLibrary" />
    </Module>
    ```

     테마의 경우 기존 모듈 태그를 다음 태그로 바꿉니다.

    ```xml
    <Module Name="[Module Name]" Url="_catalogs/theme"
        <File Path="[Module Name]\[Theme Name].thmx" Url="[Theme
          Name].thmx" Type="GhostableInLibrary" />
    </Module>
    ```

     모듈 및 마스터 페이지 또는 테마의 실제 이름을 사용 하 여 자리 표시자 값을 대체 해야 합니다.

     특성 `Type="GhostableInLibrary"` 콘텐츠 데이터베이스에 항목 추가 나타냅니다 및 `Url` 모듈의 특성은 SharePoint 콘텐츠 데이터베이스에 파일을 저장할 위치를 지정 합니다.

11. 마스터 페이지에 대 한 배포 범위를 변경 하려면 **솔루션 탐색기**기능 디자이너에서 기능 파일을 열고, 및에서 새 배포 범위를 선택 합니다 **범위** 목록입니다.

     값이 **웹** 마스터 페이지는 현재 프로젝트에 지정 된 웹 사이트에만 적용 되는 것을 의미 합니다. 값이 **사이트** 마스터 페이지 모든 하위 사이트와 웹 루트를 포함 하는 현재 사이트 컬렉션에 적용 하는 것을 의미 합니다. 다른 값이 적용 되지 않습니다.

    > [!NOTE]
    > 사이트 모음 수준에만 테마를 적용할지, 때문에 설정 하지 않으면 테마의 범위에 아무 것도 아닌 다른 것이 좋습니다 **사이트**합니다. 하위 사이트에 테마를 사용 하는 경우 오류가 발생할 수 있습니다.

12. 메뉴 모음에서 선택 **빌드합니다** > **솔루션 배포**합니다.

13. 파일을 올바르게 배포 되었는지 여부를 확인 하려면 SharePoint 사이트를 열고, 선택는 **사이트 작업** 메뉴에서 선택 합니다 **사이트 설정** 명령을 실행 하 고 다음 중 하나를 선택는 **마스터 페이지**  링크 또는 **테마** 링크 합니다.

     마스터 페이지 또는 테마 목록 표시 되 고 가져온 테마 또는 마스터 페이지를 포함 합니다.

## <a name="see-also"></a>참고자료
- [마스터 페이지](http://go.microsoft.com/fwlink/?LinkId=184955)
- [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint에 대 한 페이지 만들기](../sharepoint/creating-pages-for-sharepoint.md)
- [모듈을 사용 하 여 솔루션에 파일을 포함](../sharepoint/using-modules-to-include-files-in-the-solution.md)
