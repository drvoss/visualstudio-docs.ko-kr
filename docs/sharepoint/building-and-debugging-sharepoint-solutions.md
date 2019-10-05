---
title: SharePoint 솔루션 빌드 및 디버깅 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e91c1433fde85a9ec828a6a018bee986fdc7aa5c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62988133"
---
# <a name="build-and-debug-sharepoint-solutions"></a>빌드 및 SharePoint 솔루션 디버깅
  일반적으로 SharePoint 솔루션 빌드 및 디버깅 같습니다 빌드 및 기타 유형의 프로젝트를 디버깅 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. 이 섹션의 항목에서는 차이점에 대해 설명합니다.

## <a name="project-output-for-sharepoint-solutions"></a>SharePoint 솔루션에 대 한 프로젝트 출력
 어셈블리 및 솔루션 패키지를 만들 SharePoint 솔루션 구축 ( *.wsp*) 파일입니다. 다음 표에서 빌드하는 동안 이러한 파일의 위치를 보여 줍니다.

|항목 빌드|출력 폴더|
|----------------|-------------------|
|어셈블리, 프로그램 데이터베이스 ( *.pdb*), 및 *.wsp* 파일입니다.|*\<프로젝트 이름 > \bin\debug* 나  *\<ProjectName > \bin\release*|
|SharePoint 프로젝트 항목 파일입니다.|*\<프로젝트 이름 > \pkg\debug* 나  *\<ProjectName > \pkg\release*|
|중간 파일을 빌드하십시오.|*\<프로젝트 이름 > \obj\debug* 나  *\<ProjectName > \obj\release*|
|중간 파일을 패키지 합니다.|*\<프로젝트 이름 > \pkgobj\debug* 나  *\<ProjectName > \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>SharePoint 솔루션 빌드
 SharePoint 솔루션을 빌드하려면 개발 컴퓨터에 올바른 버전의 SharePoint server 설치 되어 있어야 합니다. 이 고, 그렇지 SharePoint 솔루션을 빌드하는 다른 형식의 프로젝트를 빌드하는 것과 동일한 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]입니다. 자세한 내용은 [방법: SharePoint 솔루션 빌드](../sharepoint/how-to-build-sharepoint-solutions.md)합니다.

## <a name="debug-and-test-sharepoint-solutions"></a>SharePoint 솔루션을 테스트 및 디버그
 디버깅 하기 전에 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 복사본은 *.wsp* SharePoint 서버에 패키지 사이트 및 웹 범위 기능을 활성화 하 고 경우에 따라 프로젝트를 시작 합니다. 수동으로 프로젝트를 열어야 하는 경우도 있습니다. 자세한 내용은 [문제를 해결 하는 SharePoint 솔루션](../sharepoint/troubleshooting-sharepoint-solutions.md) 하 고 [디버그 SharePoint 솔루션](../sharepoint/debugging-sharepoint-solutions.md)합니다.

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Azure DevOps 서비스 기능을 사용 하 여 SharePoint 솔루션을 확인 및 디버그
 단위 테스트 및 IntelliTrace와 같은 azure DevOps 서비스 기능 사용 SharePoint 솔루션에서 문제를 더 정확 하 게 찾아낼 수 있습니다. 프로파일링을 통해 SharePoint 솔루션에서 성능 문제 영역을 찾고 식별할 수 있습니다. 자세한 내용은 [코드 확인 및 디버깅 SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) 하 고 [성능의 SharePoint 응용 프로그램을 프로 파일링](../sharepoint/profiling-the-performance-of-sharepoint-applications.md)합니다.

## <a name="security-during-the-build-process"></a>빌드 프로세스 중 보안
 패키지 또는 SharePoint 솔루션 배포 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 서버 파일을 복사할 수 있는 권한이 있어야 합니다. 실행 해야 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 권한 상승된 된 프로세스와 사용자 계정을 SharePoint 서버에서 사이트 컬렉션 관리자 여야 합니다. 또한 프로젝트를 샌드박스 솔루션 또는 팜 솔루션 인지 지정 해야 합니다. 자세한 내용은 [Differences Between Sandboxed and Farm Solutions](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)합니다.

## <a name="using-the-clean-command"></a>정리 명령 사용
 SharePoint 솔루션 디버깅을 위해 SharePoint 서버에 설치 된 경우는 **정리** 명령 솔루션을 제거 하지 않습니다. 대신 SharePoint 구성을 통해 기능을 비활성화 해야 합니다.

## <a name="see-also"></a>참고자료
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
- [서버 탐색기를 사용 하 여 SharePoint 연결 찾아보기](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [패키지 및 SharePoint 솔루션 배포](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
