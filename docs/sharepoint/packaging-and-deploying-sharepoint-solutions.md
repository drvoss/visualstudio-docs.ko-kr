---
title: SharePoint 솔루션 패키징 및 배포 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- packaging [SharePoint development in Visual Studio]
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, packaging and deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4c187865518c9556d63d9e5e632ec5c658fc3e0f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953506"
---
# <a name="package-and-deploy-sharepoint-solutions"></a>패키지 및 SharePoint 솔루션 배포
  일반적으로 솔루션 패키지 (.wsp) 파일을 사용 하 여 SharePoint 솔루션을 SharePoint 서버에 배포 됩니다. 기능으로 SharePoint 프로젝트 항목을 구성 하 고 SharePoint 기능을 배포 하는 패키지를 만들려면 Visual Studio를 사용할 수 있습니다.

 이 항목에서는 다음 내용에 대해 설명합니다.

- [기능 및 패키지 만들기](#create-features-and-packages)

- [기능 및 패키징 도구 지원](#feature-and-packaging-tool-support)

- [SharePoint 솔루션 배포](#deploy-sharepoint-solutions)

- [SharePoint 솔루션에서 파일 배포](#deploy-files-in-sharepoint-solutions)

## <a name="create-features-and-packages"></a>기능 및 패키지 만들기
 Visual Studio를 사용 하 여 관련된 SharePoint 요소를 그룹화 하는 *기능*합니다. 예를 들어 연락처 목록 정의 대 한 기능 목록 정의와 목록 인스턴스를 포함할 수 있습니다. 배포를 위해 단일 기능에 이러한 두 요소를 결합할 수 있습니다. 기능에 대 한 자세한 내용은 참조 하세요. [문서 블록: 기능](http://go.microsoft.com/fwlink/?LinkID=169183)합니다.

 다음으로, SharePoint 솔루션 패키지를 만들 수 있습니다 (*.wsp*) 여러 기능을 번들을 사이트 정의 어셈블리 및 다른 파일 형식으로 SharePoint에서 파일을 배포 하는 데 필요한 파일을 저장 하는 단일 패키지로 서버입니다. 자세한 내용은 참조 하세요. [문서 블록: 솔루션](http://go.microsoft.com/fwlink/?LinkID=169186)합니다.

## <a name="feature-and-packaging-tool-support"></a>기능 및 패키징 도구 지원
 신속 하 게 기능에 쉽게 배포에 대 한 솔루션 패키지 파일을 SharePoint를 구성에 Visual Studio에서 SharePoint 개발 도구를 사용할 수 있습니다. 기능 및 솔루션 패키지를 구성 하려면 다음 도구를 사용할 수 있습니다.

- 디자이너 및 패키지 디자이너 기능입니다.

- 패키징 탐색기, 도구 창입니다.

- 솔루션 탐색기입니다.

### <a name="feature-designer-and-package-designer"></a>기능 디자이너 및 패키지 디자이너
 기능 만들기 하 고, 범위를 설정 하 고, 기능 디자이너를 사용 하 여 다른 기능 종속성으로 표시할 수 있습니다. 디자이너는 또한 각 기능을 설명 하는 최종 XML 파일을 표시 합니다. 자세한 내용은 [만들 SharePoint 기능](../sharepoint/creating-sharepoint-features.md)합니다.

 기능을 설정 하 여 특정 웹 사이트 또는 웹 사이트의 그룹에 적용할 해당 *범위* 기능 디자이너에서 합니다. 개별 웹 사이트에 대 한 기능이 활성화 된 경우 기능이 해당 특정 웹 사이트 에서만 작동 합니다. 사이트 모음 기능 활성화 되 면 전체 사이트 컬렉션에 항목 기능에 적용 됩니다. 자세한 내용은 [요소 범위](http://go.microsoft.com/fwlink/?LinkID=169189)합니다.

 다른 기능에도 다른 여러 가지 기능을 사용 하는 경우 설정할 수 있습니다는 *기능 활성화 종속성* 기능을 사용할 수 있도록 설정 하기 전에 종속 기능을 표시 합니다. 기능 활성화 종속성 종속 기능 해당 범위에 이미 활성화 되어 확인 합니다. 자세한 내용은 [활성화 종속성 및 범위](http://go.microsoft.com/fwlink/?LinkID=169190)합니다.

 패키지 디자이너에서 SharePoint 요소를 단일 솔루션 패키지를 그룹화 하 고를 배포 하는 동안 웹 서버를 다시 설정할지를 구성할 수 있습니다. 배포 서버 유형을 설정 하려면 사용 합니다 **속성** 창입니다. 또한 디자이너는 패키지 콘텐츠를 설명 하는 XML 파일을 생성 합니다. 자세한 내용은 [만들 SharePoint 솔루션 패키지](../sharepoint/creating-sharepoint-solution-packages.md)합니다.

 배포 하는 동안 인터넷 정보 서비스 (IIS) 서비스는 SharePoint 서버에 솔루션 파일을 복사할 중지 됩니다. Visual Studio에서 패키지 디자이너를 사용 하면 웹 서버를 다시 시작 해야 하는지 여부를 선택할 수 있습니다. 솔루션은 프런트 엔드 웹 서버 또는 응용 프로그램 서버에 배포 되는 경우를 구성 하려면 사용 합니다 **속성** 창입니다. 자세한 내용은 [Solution 요소 (Solution)](http://go.microsoft.com/fwlink/?LinkID=169191)합니다.

### <a name="packaging-explorer"></a>패키징 탐색기
 기능 디자이너 및 패키지 디자이너를 보완 하기 위해 파일을 그룹화 하려면 SharePoint 기능 및 패키지에 패키징 탐색기를 사용할 수 있습니다. 패키지에 기능을 SharePoint 프로젝트의 계층적 뷰를 볼 수는 또한 항목 및 파일입니다. 패키징 탐색기는 다음 작업을 완료 하는 데 사용할 수 있는 도구 창:

- SharePoint 프로젝트 항목 및 파일을 엽니다.

- 다른 기능 중 하나에서 SharePoint 프로젝트 항목을 끌어서 설정.

- SharePoint 프로젝트 항목 및 끌어서 기능 한 패키지에서 간에 합니다.

- 패키지에 새 기능을 추가 합니다.

- 기능 또는 패키지 디자이너를 엽니다.

- 기능 및 패키지의 유효성을 검사 합니다.

  Visual Studio에서 SharePoint 개발 도구는 솔루션 패키지를 올바른 형식 인지 확인 하려면 유효성 검사 규칙이 있습니다. 또한 규칙을 확인 하는 *.wsp* 솔루션 파일을 성공적으로 배포 하 고 SharePoint 서버에서 활성화 있습니다. 기능에 대 한 XML 스키마에 대 한 자세한 내용은 참조 하세요 [기능 스키마](http://go.microsoft.com/fwlink/?LinkID=169192)합니다.

  SharePoint 프로젝트 시스템에 사용자 지정 기능 및 패키지 유효성 검사 규칙을 추가할 수 있습니다. 자세한 내용은 [방법: SharePoint 솔루션에 대 한 유효성 검사 규칙 사용자 지정 기능 및 패키지를 만들](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)합니다.

  패키징 탐색기에 대 한 자세한 내용은 참조 하세요. [방법: 추가 및 패키징 탐색기를 사용 하 여 패키지에 기능과 항목 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md)합니다.

### <a name="solution-explorer"></a>솔루션 탐색기
 솔루션 탐색기를 사용 하 여 탐색 하 고 SharePoint 프로젝트의 파일을 열 수 있습니다. 솔루션 탐색기에서 상황에 맞는 메뉴를 사용 하 여 기능을 기능 이벤트 수신자를 추가 하 고 리소스 기능. 또한 기능 및 배포에 대 한 패키지를 구성 하는 기능 디자이너 및 패키지 디자이너를 열 수 있습니다.

## <a name="deploy-sharepoint-solutions"></a>SharePoint 솔루션 배포
 기능 및 Visual Studio에서 패키지를 사용자 지정 후 만들 수 있습니다는 *.wsp* SharePoint 서버를 배포 하는 파일입니다. Visual Studio를 사용 하 여 디버깅 하 고 테스트 합니다. *wsp* 개발 컴퓨터에 SharePoint 서버에만 합니다. 원격 SharePoint 서버에 SharePoint 솔루션을 배포 하는 방법에 대 한 자세한 내용은 참조 하세요. [솔루션을 배포](http://go.microsoft.com/fwlink/?LinkID=169194)합니다.

 또한 개발 컴퓨터의 배포 단계를 사용자 지정할 수 있습니다. 자세한 내용은 [배포를 게시 하 고 SharePoint 솔루션 패키지를 업그레이드](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)합니다.

## <a name="deploy-files-in-sharepoint-solutions"></a>SharePoint 솔루션에서 파일 배포
 일반적으로 SharePoint 프로젝트 항목을 SharePoint 솔루션에 추가할 때 필요한 모든 파일이 포함 됩니다. 파일을 컴파일된 (코드 파일) 솔루션의 출력 어셈블리에 빌드됩니다. 그러나 예를 들어 호환 되지 않은 파일을 추가 해야 수도 *.xml*를 *.txt*, 또는 SharePoint 프로젝트에 리소스 파일입니다. 이러한 파일은 솔루션에서 자동으로 패키지 되지 않습니다. 패키지 되도록 추가 하거나 파일이 매핑된 폴더 또는 SharePoint 프로젝트 항목입니다.

 솔루션을 배포할 때 SharePoint hive 매핑된 폴더에 추가 된 파일 자동으로 복사 됩니다. SharePoint 프로젝트 항목에 추가 된 파일에 지정 된 위치에 배포 되는 **배포 위치** 부분적으로 설정 되는 각 파일에 대 한 속성에 따라 합니다 **배포 유형** 속성. 기본적으로 **배포 유형** 속성 값이 **NoDeployment**, 즉, 파일을 솔루션으로 배포 되지 않은 합니다. 패키지에 파일을 포함 하도록 속성에 대 한 다른 값을 설정 해야 합니다.

 예를 들어, 추가 하는 *.xml* SharePoint 프로젝트에 파일을 이러한 작업 중 하나를 수행 합니다.

- SharePoint "레이아웃" 매핑된 폴더를 프로젝트에 추가 합니다. 이렇게 **솔루션 탐색기** 라는 폴더 **레이아웃** 프로젝트에 대 한 하위 폴더 포함 합니다. 추가 된 *.xml* 새 하위 폴더에는 파일입니다. 기본적으로 파일에서 SharePoint 파일 시스템에 배포 된 *... \TEMPLATE\LAYOUTS\\\<폴더 이름 >* 합니다. 매핑된 폴더를 추가 하는 방법에 대 한 정보를 참조 하세요 [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)합니다.

- 추가 합니다 *.xml* SharePoint 프로젝트 항목의 폴더에 파일을 변경한를 **배포 유형을** 의 속성을 *.xml* 에서 파일 **NoDeployment**  와 같은 다른 설정과 **RootFile** 하거나 **ElementFile**합니다. 적절 한 **배포 유형을** 설정 파일과 프로젝트에 따라 달라 집니다. 에 대 한 자세한 내용은 합니다 **배포 유형을** 속성 설정을 참조 하세요 [SharePoint 개발 솔루션](../sharepoint/developing-sharepoint-solutions.md)합니다.

  추가 파일을 솔루션의 특정 프로젝트에 적용 되지 않는 경우에 빈 SharePoint 프로젝트를 솔루션에 추가 하 고에 파일을 추가할 수 있습니다. 콘텐츠 데이터베이스에 특히 SharePoint에 파일을 배포 하기 위한 또 다른 방법은 프로젝트에 모듈을 추가 하 고 다음 모듈에 파일을 추가 하는 것입니다. 자세한 내용은 [모듈을 사용 하 여 솔루션에 파일을 포함](../sharepoint/using-modules-to-include-files-in-the-solution.md)합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
