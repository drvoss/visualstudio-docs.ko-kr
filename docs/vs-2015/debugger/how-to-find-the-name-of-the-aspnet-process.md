---
title: '방법: ASP.NET 프로세스의 이름 찾기 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 53072013c1665687262d30f4a0c2720641c920be
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685947"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>방법: ASP.NET 프로세스의 이름 찾기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

실행 중인 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션에 연결하려면 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 프로세스의 이름을 알고 있어야 합니다.  
  
- IIS 6.0 또는 IIS 7.0을 실행하는 경우 이 이름은 w3wp.exe입니다.  
  
- 이전 버전의 IIS를 실행하는 경우 이 이름은 aspnet_wp.exe입니다.  
  
  사용 하 여 빌드된 응용 프로그램에 대 한 [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] 이상 버전는 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 코드 파일 시스템에 상주 하 고 WebDev.WebServer.exe 테스트 서버에서 실행할 수 있습니다. 이 경우 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 프로세스가 아닌 WebDev.WebServer.exe에 연결해야 합니다. 이 시나리오는 로컬 디버깅에만 적용됩니다.  
  
  이전 버전의 ASP 애플리케이션은 in-process로 실행되는 경우 IIS 프로세스 inetinfo.exe 내에서 실행됩니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>프로젝트 코드가 파일 시스템에 상주하는지 아니면 IIS에 상주하는지 확인하려면  
  
1. Visual Studio에서 엽니다 **솔루션 탐색기** 열려 있지 않으면입니다.  
  
2. 애플리케이션의 이름이 들어 있는 최상위 노드를 선택합니다.  
  
3. 경우는 **속성** 파일 경로 포함 하는 창 제목, 응용 프로그램 코드는 파일 시스템에 상주 합니다.  
  
     그렇지 않으면 합니다 **속성** 창 제목에는 웹 사이트의 이름이 포함 됩니다.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>애플리케이션이 실행되는 IIS 버전을 확인하려면  
  
1. 찾을 **관리 도구** 하 고 실행 합니다. 이 운영 체제에 따라 내의 아이콘이 표시 될 수 있습니다 **Control Panel**, 또는 클릭 하면 나타나는 메뉴 항목 **시작**합니다.  
  
     Windows xp에서 **제어판** 종류별 보기나 클래식 보기로에 있을 수 있습니다. 종류별 보기를 클릭 해야 **클래식 보기로 전환** 또는 **성능 및 유지 관리** 보려는 합니다 **관리 도구** 아이콘입니다.  
  
2. **관리 도구**, 인터넷 정보 서비스를 실행 합니다. MMC 대화 상자가 나타납니다.  
  
3. 왼쪽 창에 컴퓨터 목록이 표시되면 애플리케이션 코드가 상주하는 컴퓨터를 선택합니다.  
  
4. IIS 버전에는 **버전** 오른쪽 창의 열입니다.  
  
## <a name="see-also"></a>참고 항목  
 [웹 응용 프로그램 원격 디버깅의 필수 구성 요소](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [시스템 요구 사항](../debugger/aspnet-debugging-system-requirements.md)   
 [ASP.NET 디버그 준비](../debugger/preparing-to-debug-aspnet.md)   
 [웹 애플리케이션 및 스크립트 디버그](../debugger/debugging-web-applications-and-script.md)
