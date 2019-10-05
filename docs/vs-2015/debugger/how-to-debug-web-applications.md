---
title: '방법: 웹 응용 프로그램 디버그 | Microsoft Docs'
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
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd3cbbcd740c0f124b8ab4379204a9d425cd541c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205397"
---
# <a name="how-to-debug-web-applications"></a>방법: 웹 애플리케이션 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 응용 프로그램을 개발 하기 위한 기본 기술 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 디버거에서는 로컬 컴퓨터 또는 원격 서버에서 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 애플리케이션을 디버깅하는 강력한 도구를 제공합니다. 이 항목에서는 디버그 하는 방법을 설명를 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 프로젝트 개발 중입니다. 디버깅 하는 방법에 대 한 자세한를 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 웹 프로덕션 서버에 이미 배포 된 응용 프로그램을 참조 하십시오 [배포 된 웹 응용 프로그램 디버깅](../debugger/debugging-deployed-web-applications.md)합니다.  
  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션을 디버깅하려면  
  
- 필요한 권한이 있어야 합니다. 자세한 내용은 [System Requirements](../debugger/aspnet-debugging-system-requirements.md)항목을 참조하세요.  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 디버깅에 사용할 수 있어야 합니다 **프로젝트 속성**합니다.  
  
- 애플리케이션의 구성 파일(Web.config)이 디버그 모드로 설정되어 있어야 합니다. 디버그 모드를 설정하면 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]에서 동적으로 생성된 파일에 대한 기호를 만들고 디버거가 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 애플리케이션에 연결할 수 있도록 합니다. 웹 프로젝트 템플릿에서 프로젝트를 만든 경우 디버깅을 시작하면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]가 이를 자동으로 설정합니다.  
  
- 자세한 내용은 [방법: ASP.NET 응용 프로그램에 디버깅 사용](../debugger/how-to-enable-debugging-for-aspnet-applications.md)합니다.  
  
### <a name="to-debug-a-web-application-during-development"></a>개발하는 동안 웹 애플리케이션을 디버깅하려면  
  
1. 에 **디버그** 메뉴에서 클릭 **시작** 웹 응용 프로그램 디버깅을 시작 합니다.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 웹 응용 프로그램 프로젝트를 빌드하고 필요한 경우 이 응용 프로그램을 배포한 다음, 사용자가 로컬로 디버깅하는 경우 ASP.NET Development Server를 시작하고 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 작업자 프로세스에 연결합니다.  
  
2. 다른 애플리케이션을 디버깅할 때처럼 디버거를 사용하여 중단점을 설정하거나 지우고 단계별로 실행하며 기타 디버깅 작업을 수행합니다.  
  
     자세한 내용은 [디버거 기본 사항](../debugger/debugger-basics.md)합니다.  
  
3. 에 **디버그** 메뉴에서 클릭 **디버깅 중지** 디버깅 세션을 종료 하거나에 **파일** Internet Explorer의 메뉴 클릭 **닫기**합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Debugging Web Applications and Script](../debugger/debugging-web-applications-and-script.md) (웹 응용 프로그램 및 스크립트 디버그)  
 [ASP.NET 및 AJAX 애플리케이션 디버그](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [방법: ASP.NET 애플리케이션에 디버깅 사용](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
