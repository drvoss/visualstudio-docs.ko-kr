---
title: SharePoint 솔루션 보안 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- security [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, security
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 31bcd41dc1a6fd7f314c7d701f52c3728dd2ee8c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009805"
---
# <a name="security-for-sharepoint-solutions"></a>SharePoint 솔루션 보안
  [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 응용 프로그램의 보안을 강화 하는 데 도움이 되는 다음과 같은 기능이 통합 되어 있습니다.

## <a name="safe-control-entries"></a>안전 컨트롤 항목
 모든 SharePoint 프로젝트 항목에서 만든 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에 **안전 컨트롤 항목** 안전을 나타내는 속성 컬렉션을 제어 합니다. 해당 **안전한** 하위 속성을 사용 하면 보안 생각 되는 컨트롤을 지정할 수 있습니다. 자세한 내용은 [프로젝트 항목에 패키지 및 배포 정보를 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) 하 고 [안전한 웹 파트 지정](http://go.microsoft.com/fwlink/?LinkId=177521)합니다.

## <a name="allowpartiallytrustedcallers-attribute"></a>AllowPartiallyTrustedCallers 특성
 기본적으로 런타임 코드 액세스 보안 (CA) 시스템에서 완전히 신뢰할 수 있는 응용 프로그램만 공유 관리 코드 어셈블리를 액세스할 수 있습니다. AllowPartiallyTrustedCallers 특성을 사용 하 여 완전 신뢰 어셈블리를 표시 합니다. 부분적으로 신뢰할 수 있는 어셈블리를 액세스할 수 있습니다.

 AllowPartiallyTrustedCallers 특성 시스템 전역 어셈블리 캐시에 배포 되지 않은 모든 SharePoint 솔루션에 추가 됩니다 ( [!INCLUDE[TLA2#tla_gac](../sharepoint/includes/tla2sharptla-gac-md.md)]). 샌드박스 솔루션 또는 SharePoint 응용 프로그램 Bin 디렉터리에 배포 된 솔루션 포함. 자세한 내용은 [for Microsoft.NET Framework 버전 1 보안 변경 내용](http://go.microsoft.com/fwlink/?LinkId=177515) 하 고 [SharePoint Foundation에서 웹 파트 배포](http://go.microsoft.com/fwlink/?LinkId=177509)합니다.

## <a name="safe-against-script-property"></a>스크립트 속성에 대해 안전
 *삽입 스크립트* 컨트롤이 나 웹 페이지에 악성 코드 삽입 됩니다. 스크립트 삽입에 대 한 SharePoint 2010 사이트를 보호 하기 위해, 참가자 보거나 기본적으로 웹 파트 또는 해당 속성을 편집할 수 없습니다. 이 동작은 SafeAgainstScript 호출 SafeControl 특성에 의해 제어 됩니다. [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 프로젝트 항목의에이 특성을 설정 **안전 컨트롤 항목** 하위 **스크립트에 대해 안전**합니다. 자세한 내용은 [프로젝트 항목에 패키지 및 배포 정보 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) 및 [방법: 컨트롤로 표시 안전](../sharepoint/how-to-mark-controls-as-safe-controls.md)합니다.

## <a name="vista-and-windows-7-user-account-control"></a>Vista 및 Windows 7 사용자 계정 컨트롤
 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 및 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 사용자 계정 컨트롤 (UAC)으로 알려진 보안 기능을 통합 합니다. SharePoint 솔루션을 개발 하 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에 [!INCLUDE[windowsver](../sharepoint/includes/windowsver-md.md)] 하 고 [!INCLUDE[win7](../sharepoint/includes/win7-md.md)] 시스템의 경우 UAC를 실행 해야 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 시스템 관리자로 합니다. **시작** 메뉴에서 바로 가기 메뉴를 열고 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 선택한 후 **관리자 권한으로 실행**합니다.

 구성 하는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 항상 관리자 권한으로 실행, 해당 바로 가기 메뉴를 열고, 선택 바로 가기 **속성**를 선택 합니다 **고급** 단추를 **속성**대화 상자에서 선택한 후는 **관리자 권한으로 실행** 확인란 합니다.

 자세한 내용은 [이해 및 Windows Vista의 사용자 계정 컨트롤 구성](http://go.microsoft.com/fwlink/?LinkID=156476)합니다. 및 [Windows 7 사용자 계정 컨트롤](http://go.microsoft.com/fwlink/?LinkId=177523)합니다.

## <a name="sharepoint-permissions-considerations"></a>SharePoint 사용 권한 고려 사항
 SharePoint 솔루션을 개발 하려면 실행 하 고 SharePoint 솔루션을 디버깅할 충분 한 권한이 있어야 합니다. SharePoint 솔루션을 테스트할 수 있습니다, 전에 필요한 권한이 있는지 확인 하려면 다음 단계를 수행 합니다.

1. 시스템에서 관리자 권한으로 사용자 계정을 추가 합니다.

2. 팜 관리자는 SharePoint 서버에 대 한 사용자 계정에 추가 합니다.

    1. SharePoint 2010 중앙 관리에서 선택 합니다 **팜 관리자 그룹 관리** 링크 합니다.

    2. 에 **Farm Administrators** 페이지를 선택 합니다 **새로 만들기** 메뉴 옵션

3. 사용자 계정에 추가 된 권한을 WSS_ADMIN_WPG 그룹에 있습니다.

## <a name="additional-security-resources"></a>추가 보안 리소스
 보안 문제에 대 한 자세한 내용은 다음을 참조 합니다.

### <a name="visual-studio-security"></a>Visual Studio 보안

- [보안 및 사용자 권한](http://go.microsoft.com/fwlink/?LinkId=177503)

- [네이티브 및.NET Framework 코드의 보안](http://go.microsoft.com/fwlink/?LinkId=177504)

- [.NET Framework의 보안](http://go.microsoft.com/fwlink/?LinkId=177502)

### <a name="sharepoint-security"></a>SharePoint 보안

- [SharePoint Foundation 관리 및 보안](http://go.microsoft.com/fwlink/?LinkId=177501)

- [SharePoint 보안 리소스 센터](http://go.microsoft.com/fwlink/?LinkId=177498)

- [SharePoint Foundation에서 웹 파트 보안](http://go.microsoft.com/fwlink/?LinkId=177511)

- [웹 응용 프로그램 보안 개선: 위협 및 대책](http://go.microsoft.com/fwlink/?LinkID=140080)

### <a name="general-security"></a>일반적인 보안

- [MSDN 보안 개발 수명 주기](http://go.microsoft.com/fwlink/?LinkID=147149)

- [보안 된 ASP.NET 응용 프로그램 빌드: 인증, 권한 부여 및 보안 통신](http://go.microsoft.com/fwlink/?LinkId=177494)

## <a name="see-also"></a>참고자료

- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)