---
title: 로컬 SharePoint 사이트에 SharePoint 솔루션을 게시 및 배포
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3e68fc4e49311535169ab37a2332b443ba632fb5
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401462"
---
# <a name="how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site"></a>방법: 배포 하 고 로컬 SharePoint 사이트에 SharePoint 솔루션을 게시 합니다.
  배포 하거나 개발 컴퓨터의 로컬 SharePoint 서버에 SharePoint 솔루션을 게시할 수 있습니다. 배포 프로세스 복사 합니다 *.wsp* 파일을 SharePoint 서버 솔루션을 설치 하 고 다음 기능을 활성화 합니다. 게시 복사본에만 처리 합니다 *.wsp* 파일을 SharePoint 서버 설치 합니다. SharePoint에서 사용 하도록 설정 하는 것을 수동으로 활성화 해야 합니다.

## <a name="to-deploy-a-sharepoint-solution-to-the-local-sharepoint-server"></a>로컬 SharePoint 서버에 SharePoint 솔루션을 배포 하려면

1. **솔루션 탐색기**를 배포 하려는 프로젝트를 선택 합니다.

2. 메뉴 모음에서 **빌드**하십시오 **솔루션 배포**합니다.

     합니다 *.wsp* 파일을 만들고 로컬 SharePoint 서버에 설치 합니다. 또한 기능 활성화 됩니다.

## <a name="to-publish-a-sharepoint-solution-to-a-local-sharepoint-server"></a>로컬 SharePoint 서버에 SharePoint 솔루션을 게시 하려면

1. **솔루션 탐색기**에 게시 하 고 선택 하려는 SharePoint 프로젝트에 대 한 바로 가기 메뉴를 열고 **게시**합니다.

2. 에 **게시** 대화 상자를 선택 합니다 **파일 시스템에 게시** 옵션 단추입니다.

3. 에 **대상 위치** 텍스트 상자에 로컬 경로 입력 하 고 선택한 합니다 **게시** 단추입니다.

     Visual Studio에 게시 진행률이 나타납니다 **출력** 창입니다. 프로세스가 완료 되 면, 솔루션 ( *.wsp*) 파일이 로컬 SharePoint 서버에 설치 됩니다. 그러나 여전히 활성화 되어야 합니다 SharePoint에서 사용할 수 있습니다. 솔루션 파일이 이미 있는 경우 오류가 발생 하 고 기존 파일을 덮어쓸 것인지 여부를 묻습니다. 원격 패키지를 업그레이드에서 업그레이드 패키지에 대 한 자세한 내용은 섹션을 참조 [방법: 배포, 게시 및 원격 서버에 SharePoint 솔루션 업그레이드](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)합니다.

## <a name="see-also"></a>참고자료
- [방법: 배포, 게시 및 원격 서버에 SharePoint 솔루션 업그레이드](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)
- [SharePoint 솔루션 패키지 만들기](../sharepoint/creating-sharepoint-solution-packages.md)
- [방법: SharePoint 솔루션 패키지 사용자 지정](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)
- [방법: 추가 및 패키지 디자이너를 사용 하 여 패키지에 기능과 항목 제거](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)
