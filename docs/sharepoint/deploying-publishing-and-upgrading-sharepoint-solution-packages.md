---
title: 배포, 게시 및 SharePoint 솔루션 패키지를 업그레이드 합니다.
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Project.SharePointProjectPropertyTab
- VS.SharePointTools.Project.Publishing
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
ms.openlocfilehash: 7c41b36766e112dc86bd15c7a2bec48633c35b57
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66402035"
---
# <a name="deploy-publish-and-upgrade-sharepoint-solution-packages"></a>배포, 게시 및 SharePoint 솔루션 패키지를 업그레이드 합니다.
  Visual Studio에서 SharePoint 솔루션을 개발한 후 로컬 SharePoint 서버에 해당 패키지 (.wsp) 파일을 배포 하거나 원격 또는 로컬 SharePoint 서버에 게시 합니다. 파일을 배포 하는 경우 패키지 파일 (.wsp) 배포 되는 방식을 사용자 지정할 수 있습니다.

> [!NOTE]
> 현재 원격 SharePoint 서버에만 샌드박스 솔루션을 게시할 수 있습니다. 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)합니다.

## <a name="deploy-publish-and-upgrade"></a>배포, 게시 및 업그레이드
 *배포* 은 로컬 호스트에 Visual Studio에서 SharePoint 프로젝트에서 빌드된 SharePoint 솔루션 파일을 복사를 의미 합니다. 배포 된 솔루션에서는 솔루션 배포 후 활성화 인터넷 정보 서비스 (IIS) 풀을 재활용 하는 등 배포 단계를 구성 하 고 등 수 있습니다. 를 배포 하려면 사용 합니다 **배포** 명령을 합니다 **빌드** 메뉴. 자세한 내용은 [방법: SharePoint 배포 구성 편집](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) 고 [방법: 배포 하 고 로컬 SharePoint 사이트에 SharePoint 솔루션을 게시](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)합니다.

 *게시* 샌드박스 SharePoint 솔루션 파일을 원격 sharepoint 업로드에 참조 사이트, 즉 다른 시스템에 있는 사이트입니다. 또한 SharePoint 샌드박스 솔루션 파일을 로컬 SharePoint 사이트에 게시할 수는 있지만 여부에 관계 없이 사이트에 게시 된 로컬 또는 원격에 배포 단계를 구성할 수 없습니다.

 *업그레이드* 기존 원격 또는 로컬로 게시 된 SharePoint 솔루션에 업데이트를 가리킵니다. Visual Studio에서 SharePoint 솔루션에 변경 된 후 솔루션의 패키지 파일 이름 변경, 솔루션을 다시 게시 및 성공적으로 게시 한 후에 다음 솔루션을 업그레이드 합니다. 로컬 게시 된 솔루션을 다시 게시 하는 경우 기존 솔루션 파일을 덮어쓸 수 있습니다.

## <a name="deploy-packages"></a>패키지 배포
 테스트 및 디버깅을 위한 개발 컴퓨터에 SharePoint 서버에 패키지 파일을 배포할 수 있습니다. 선택 하 여 다른 컴퓨터에 설치할 수 있는 패키지 파일을 만들 수도 있습니다는 **파일 시스템에 게시** 옵션 단추를 **게시** 대화 상자. 패키지를 만들고 지정 된 로컬 파일 경로에 복사 합니다. 로컬 서버에 SharePoint 솔루션을 배포 하려면 사용 합니다 **배포** 명령을 합니다 **빌드** 메뉴. 자세한 내용은 [방법: 배포 하 고 로컬 SharePoint 사이트에 SharePoint 솔루션을 게시](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)합니다.

 목록 정의 배포, 이벤트 수신기를 추가, 디자이너 기능 및 패키지 디자이너를 사용 하는 방법에 알아보려면 참조 [연습: 프로젝트 작업 목록 정의 배포](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md)합니다.

## <a name="customize-the-deployment-process"></a>배포 프로세스를 사용자 지정
 다음 표에서 디버그 하 고 SharePoint 솔루션을 배포할 때 사용할 수 있는 두 개의 배포 구성을 보여 줍니다.

|배포 구성|설명|
|------------------------------|-----------------|
|기본|기본 배포 구성입니다. 다음 배포 단계를 수행 됩니다.<br /><br /> 1.  배포 전 명령을 실행 합니다.<br />2.  IIS 응용 프로그램 풀을 재활용 합니다.<br />3.  솔루션을 취소 합니다.<br />4.  솔루션을 추가 합니다.<br />5.  기능을 활성화 합니다.<br />6.  배포 후 명령을 실행 합니다.<br /><br /> 패키지를 제거 해도 다음 취소 단계를 수행 됩니다.<br /><br /> 1.  IIS 응용 프로그램 풀을 재활용 합니다.<br />2.  솔루션을 취소 합니다.|
|정품 인증 없음|이 배포 구성은 기본 구성으로 동일한 단계를 실행 하지만 활성화 단계를 건너뜁니다.|

 단일 단계를 완료 하거나 배포 프로세스의 단계 순서를 변경 하려면 고유한 배포 구성을 만들 수 있습니다. 자세한 내용은 [방법: SharePoint 배포 구성 편집](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md)합니다.

 또한 배포 이전 및 이후에 실행할 명령을 추가할 수 있습니다. 자세한 내용은 [방법: SharePoint 배포 명령 설정](../sharepoint/how-to-set-sharepoint-deployment-commands.md)합니다.

## <a name="publish-packages-to-a-remote-or-local-server"></a>원격 또는 로컬 서버에 패키지를 게시 합니다.
 메뉴 모음에서 원격 서버에 샌드박스 SharePoint 솔루션을 게시 하려면 **빌드**, **게시**를 차례로 합니다 **게시** 대화 상자에서 선택 합니다 **SharePoint 사이트에 게시** 와 같은 원격 서버의 URL을 제공 하는 옵션 단추를 **https://someremoteserver.sharepoint.microsoftonline.com** 합니다.

 로컬 서버에 SharePoint 솔루션을 게시 하는 **게시** 대화 상자를 선택 합니다 **파일 시스템에 게시** 옵션 단추를 로컬 시스템 경로 제공 하 합니다.

 솔루션에 표시 되는 솔루션을 SharePoint에 성공적으로 게시 한 후 합니다 **솔루션 갤러리** 를 활성화할 수 있습니다. 자세한 내용은 [방법: 배포, 게시 및 원격 서버에 SharePoint 솔루션 업그레이드](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)합니다.

### <a name="upgrade-published-packages"></a>게시 된 패키지를 업그레이드 합니다.
 모든 Visual Studio에서 SharePoint 프로젝트에 게시 된 후를 변경한 경우 변경 내용을 포함 하도록 게시 된 패키지를 업그레이드 해야 합니다. 를 성공적으로 업그레이드 하려면 패키지는 고유한 이름이 있어야 합니다. 오류 경고는 기존 응용 프로그램을 업데이트 하는 경우 발생할 수 있습니다-폴링하는 SharePoint 사이트에서 동일한 이름의 패키지를 찾은 경우 파일 이름 충돌을 패키지 이름을 바꿀 수 있습니다. 다시 게시 되 고 새 패키지를 SharePoint 사이트에 표시 되 후 업그레이드할 수 있습니다. 업그레이드 된 패키지는 이전 패키지에서 데이터를 사용 하 여 솔루션을 업데이트 하 고 SharePoint에서 솔루션을 활성화 합니다. 자세한 내용은 [방법: 배포, 게시 및 원격 서버에 SharePoint 솔루션 업그레이드](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)합니다.

## <a name="see-also"></a>참고자료
- [패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
