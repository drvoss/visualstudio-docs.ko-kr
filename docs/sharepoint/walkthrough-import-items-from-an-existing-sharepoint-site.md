---
title: '연습: 기존 SharePoint 사이트에서 항목을 가져올 | Microsoft Docs'
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
ms.openlocfilehash: a2727f0f3a5f2b46c5110a33e63b102f9d26bdaf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446616"
---
# <a name="walkthrough-import-items-from-an-existing-sharepoint-site"></a>연습: 기존 SharePoint 사이트에서 항목 가져오기
  이 연습에서는 기존 SharePoint 사이트에서 항목을 가져오는 방법을 보여는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 프로젝트입니다.

 이 연습에서는 다음 작업을 수행합니다.

- 사용자 지정 사이트 열을 추가 하 여 SharePoint 사이트를 사용자 지정 (라고도 *필드*합니다.

- SharePoint 사이트를.wsp 파일로 내보내는 중입니다.

- .Wsp 파일을 가져오는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .wsp 가져오기 프로젝트를 사용 하 여 SharePoint.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] 및 SharePoint입니다.

- Visual Studio.

## <a name="customize-a-sharepoint-site"></a>SharePoint 사이트를 사용자 지정
 예를 들어 만들고 새 사이트 열을 추가 하 고 나중에 사용할 다른 하위 사이트를 만들어 SharePoint 하위 사이트를 사용자 지정 합니다. 나중에 첫 번째 하위.wsp 파일로 내보내려면를 다음.wsp 가져오기 프로젝트를 사용 하 여 두 번째 하위 사이트에 사용자 지정 사이트 열을 가져옵니다.

### <a name="to-create-and-customize-a-sharepoint-site"></a>만들고 SharePoint 사이트를 사용자 지정

1. 예: http:// 웹 브라우저를 사용 하 여 SharePoint 사이트를 엽니다<em>시스템 이름</em>/SitePages/Home.aspx 합니다.

2. 기본 SharePoint 사이트에서 하위 사이트를 열어 만듭니다는 **사이트 작업** 메뉴를 선택한 다음 **새 사이트**합니다.

3. 사이트의 **만들기** 대화 상자를 선택 합니다 **빈 사이트** 형식입니다.

4. 에 **제목** 상자에 입력 합니다 **사이트 열 테스트 1**;에 **URL 이름** 상자에 입력 합니다 **columntest1**; 다른 설정을 해당 기본값으로 둡니다 값이 있습니다. 선택 합니다 **만들기** 단추입니다.

5. 사이트를 만든 후 이동 하 고 주 사이트로 브라우저에서 http://<em>시스템 이름</em>/SitePages/Home.aspx 합니다.

6. 다시 열어 기본 SharePoint 사이트에서 빈 하위 사이트를 만듭니다는 **사이트 작업** 메뉴 선택 **새 사이트**를 선택한 후는 **빈 사이트** 형식입니다.

7. 에 **제목** 상자에 입력 합니다 **사이트 열 테스트 2**;에 **URL 이름** 상자에 입력 합니다 **columntest2**; 다른 설정을 해당 기본값으로 둡니다 값이 있습니다. 선택 합니다 **만들기** 단추입니다.

8. 첫 번째 하위 돌아갑니다 http://<em>SystemName</em>/columntest1/default.aspx 합니다.

9. 에 **사이트 작업** 메뉴 선택 **사이트 설정** 사이트 설정 페이지를 표시 합니다.

10. 에 **갤러리** 섹션을 선택 합니다 **사이트 열** 링크 합니다.

11. 맨 위에 있는 합니다 **사이트 열 갤러리** 페이지를 선택 합니다 **만들기** 단추입니다.

12. 에 **열 이름** 상자에 입력 합니다 **테스트 열**, 다른 기본값을 유지 하 고 선택한 합니다 **확인** 단추입니다.

13. 합니다 **테스트 열** 열에에서 아래에 표시 사용자 지정 열 제목 사이트 열 갤러리입니다.

## <a name="exporting-the-sharepoint-site"></a>SharePoint 사이트를 내보내기
 다음으로 SharePoint 항목 및 가져올 하려는 요소를 포함 하는 SharePoint 설치 (.wsp) 파일을 가져올 프로그램 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 프로젝트입니다. .Wsp 파일이 아직 없는 경우 다음 만들어야 기존 SharePoint 사이트에서 합니다. 예를 들어 기본 SharePoint 사이트를.wsp 파일로 내보냅니다.

> [!IMPORTANT]
> 다음 절차를 수행 하는 런타임 오류가 발생 하는 경우 SharePoint 사이트에 액세스할 수 있는 시스템에서 절차를 수행 해야 합니다.

### <a name="to-export-an-existing-sharepoint-site"></a>기존 SharePoint 사이트를 내보내려면

1. SharePoint 사이트에서 선택할 **사이트 설정** 에 **사이트 작업** 사이트 설정 페이지를 표시 하려면 탭 합니다.

2. 에 **사이트 작업** 섹션 사이트 설정 페이지의 선택 합니다 **템플릿으로 저장 사이트** 링크 합니다.

3. 에 **파일 이름** 상자에 입력 합니다 **ExampleSite**, 및를 **템플릿 이름** 상자에 입력 합니다 **예제 사이트**합니다.

4. 예를 들어 유지 합니다 **콘텐츠 포함** 확인란의 선택을 취소 합니다.

     이 확인란을 선택 하는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .wsp 파일에 목록 및 문서 라이브러리와 해당 콘텐츠를 저장 합니다. 이 기능은 일부 상황에서 유용 하지만이 예제에 대 한 필요 하지 않습니다.

5. 작업이 성공적으로 완료 되 면 선택 합니다 **솔루션 갤러리** .wsp 파일을 보려면 링크 합니다.

     이상, 열린 솔루션 갤러리 페이지를 보려면를 **사이트 작업** 메뉴에서 선택 **사이트 설정**를 선택 합니다 **최상위 사이트 설정으로 이동** 링크를  **사이트 컬렉션 관리** 섹션을 선택한 후 합니다 **솔루션** 링크를 **갤러리** 섹션입니다.

6. 솔루션 갤러리에서 선택 합니다 **ExampleSite** 링크 합니다.

7. 에 **파일 다운로드** 대화 상자를 선택 합니다 **저장** 다운로드 폴더에는 기본적으로 로컬 시스템에서 파일을 저장 하려면 단추입니다.

## <a name="import-the-wsp-file"></a>.Wsp 파일 가져오기
 이제는 *.wsp* 가져오기, (사용자 지정 사이트 열 테스트)를 다시 사용 하려는 항목을 포함 하는 파일을 *.wsp* 파일에 액세스할 수 합니다.

### <a name="to-import-a-wsp-file"></a>.Wsp 파일을 가져오려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 메뉴 모음에서 **파일** > **New** > **프로젝트** 표시할는 **새 프로젝트**대화 상자. IDE는 메뉴 모음에서 Visual Basic 개발 설정을 사용 하도록 설정 하는 경우 선택할 **파일** > **새 프로젝트**합니다.

2. 확장 합니다 **SharePoint** 노드 아래 **Visual C#** 또는 **Visual Basic**를 선택한 후는 **2010** 노드.

3. 선택 합니다 **SharePoint 2010 솔루션 패키지 가져오기** 에서 서식 파일을 **템플릿** 창 WspImportProject1, 프로젝트의 이름을 선택한 후는 **확인** 단추입니다.

    합니다 **SharePoint 사용자 지정 마법사** 나타납니다.

4. 에 **디버깅에 대 한 사이트 및 보안 수준을 지정** 페이지에서 입력을 [!INCLUDE[TLA2#tla_url](../sharepoint/includes/tla2sharptla-url-md.md)] 이전에 만든 두 번째 SharePoint 하위 사이트에 대 한 합니다. 새 사용자 지정 추가 필드 항목, http://<em>시스템 이름</em>해당 하위 사이트로 /columntest2.

5. 에 **이 SharePoint 솔루션의 신뢰 수준 이란?** 섹션에서 선택 항목을 그대로 둡니다 **샌드박스 솔루션으로 배포**합니다.

6. 에 **새 프로젝트 소스 지정** 페이지를 저장 하는 시스템에서 특정 위치로 이동 하는 *.wsp* 이전에 파일을 선택한를 **다음** 단추입니다.

   > [!NOTE]
   > 선택 하면를 **완료** 에서 사용 가능한 모든 항목이이 페이지에서 단추를 *.wsp* 파일을 가져옵니다.

7. 에 **가져올 항목 선택** 상자에서 모든 제외 하 고 목록에서 확인란의 선택을 취소 **테스트 열**를 선택한 후는 **마침** 단추.

    여러 항목을 포함 하는 목록에서 선택할 수 있습니다 합니다 **Ctrl**+**는** 목록의 모든 항목을 선택 하는 키를 모든 확인란의 선택을 취소 하려면 스페이스바를 선택 하 고 선택한 다음 확인만 옆의 **테스트 열** 항목입니다.

    가져오기 작업이 완료 되 면 라는 새 프로젝트 **WspImportProject1** 만들어집니다 라는 폴더를 포함 하는 **필드**합니다. 이 폴더에는 사용자 지정 사이트 열 **테스트 열** 및 해당 정의 파일이 *Elements.xml*합니다.

## <a name="deploy-the-project"></a>프로젝트 배포
 마지막으로 배포 **WspImportProject1** 두 번째 SharePoint에는 앞에서 만든 사용자 지정 사이트 열을 보려면 하위 사이트입니다.

### <a name="to-deploy-the-project"></a>프로젝트를 배포 하려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 선택 합니다 **F5** 배포 및 실행 하는 키를 *.wsp* 프로젝트 가져오기.

2. SharePoint 사이트에서 엽니다는 **사이트 작업** 메뉴를 선택한 후 **사이트 설정** 사이트 설정 페이지를 표시 합니다.

3. 에 **갤러리** 섹션을 선택 합니다 **사이트 열** 링크 합니다.

4. 아래로 스크롤하여 합니다 **사용자 지정 열** 섹션입니다.

     첫 번째 SharePoint 사이트에서 가져온 사용자 지정 사이트 열 목록에 나타나는지 확인 합니다.

## <a name="see-also"></a>참고자료
- [기존 SharePoint 사이트에서 항목 가져오기](../sharepoint/importing-items-from-an-existing-sharepoint-site.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [웹 파트 또는 응용 프로그램 페이지에 대 한 재사용 가능한 컨트롤 만들기](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
