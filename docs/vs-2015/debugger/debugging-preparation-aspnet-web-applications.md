---
title: '디버깅 준비 중: ASP.NET 웹 응용 프로그램 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7a80587062442688551d07128a2cec49a712adf6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691460"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>디버깅 준비 중: ASP.NET 웹 응용 프로그램
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]웹 사이트 템플릿은 Web Form 응용 프로그램을 만듭니다. 이 템플릿을 사용하여 웹 사이트를 만드는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서는 디버깅을 위한 기본 설정을 만듭니다. 에 **프로젝트 속성** 대화 상자에서 웹 페이지를 시작 페이지로 사용할지을 지정할 수 있습니다. 디버깅을 시작 하는 경우는 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]이러한 기본 설정 사용 하 여 웹 사이트 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Internet Explorer를 시작 하 고 디버거를 연결 합니다 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 작업자 프로세스 (aspnet_wp.exe 또는 w3wp.exe)). 자세한 내용은 [System Requirements](../debugger/aspnet-debugging-system-requirements.md)항목을 참조하세요.  
  
### <a name="to-create-a-web-forms-application"></a>Web Forms 애플리케이션을 만들려면  
  
1. 에 **파일** 메뉴 선택 **새 웹 사이트**합니다.  
  
2. 에 **새 웹 사이트** 대화 상자에서 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **웹 사이트**합니다.  
  
3. **확인**을 클릭합니다.  
  
### <a name="to-debug-your-web-form"></a>Web Form을 디버깅하려면  
  
1. 함수와 이벤트 처리기에서 하나 이상의 중단점을 설정합니다.  
  
     자세한 내용은 [Breakpoints and Tracepoints](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)을 참조하세요.  
  
2. 중단점에 도달하면 함수 내부에서 코드를 단계별로 실행합니다. 문제가 해결될 때까지 코드의 실행을 확인합니다.  
  
     자세한 내용은 [단계별 실행](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) 하 고 [웹 응용 프로그램 디버깅 및 스크립트](../debugger/debugging-web-applications-and-script.md)합니다.  
  
## <a name="changing-default-configurations"></a>기본 구성 변경  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 만든 기본 디버그 및 릴리스 구성을 변경해야 하는 경우 이를 수행할 수 있습니다. 자세한 내용은 [방법: 디버그 및 릴리스 구성 설정](../debugger/how-to-set-debug-and-release-configurations.md)을 참조하세요.  
  
#### <a name="to-change-the-default-debug-configuration"></a>기본 디버그 구성을 변경하려면  
  
1. **솔루션 탐색기**, 웹 사이트를 마우스 오른쪽 단추로 **속성 페이지** 열려는 합니다 **속성 페이지** 대화 상자.  
  
2. 클릭 **시작 옵션**합니다.  
  
3. 설정할 **시작 작업** 먼저 표시 되는 웹 페이지에 있습니다.  
  
4. 아래 **디버거**, 했는지 **ASP.NET 디버깅** 을 선택 합니다.  
  
     자세한 내용은 [웹 프로젝트에 대 한 속성 페이지 설정](../debugger/property-pages-settings-for-web-projects.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [디버거 설정 및 준비](../debugger/debugger-settings-and-preparation.md)   
 [Debugger Basics](../debugger/debugger-basics.md) (디버거 기본 사항)  
 [디버거 보안](../debugger/debugger-security.md)   
 [관리 코드 디버그](../debugger/debugging-managed-code.md)
