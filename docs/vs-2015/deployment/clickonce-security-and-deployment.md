---
title: ClickOnce 보안 및 배포 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Windows applications, ClickOnce deployment
- deploying applications [ClickOnce]
- ClickOnce deployment
- publishing, ClickOnce
ms.assetid: abab6d34-c3c2-45c1-a8b6-43c7d3131e7a
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 592bf358c24bee146290e8b3a00e28a0870f452d
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263797"
---
# <a name="clickonce-security-and-deployment"></a>ClickOnce 보안 및 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 설치 하 고 최소한의 사용자 상호 작용을 사용 하 여 실행할 수 있는 자동 업데이트 Windows 기반 응용 프로그램을 만들 수 있게 해 주는 배포 기술입니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 게시 및 Visual Basic 및 Visual C#을 사용 하 여 프로젝트를 개발한 경우 ClickOnce 기술을 사용 하 여 배포 된 응용 프로그램 업데이트에 대 한 전체 지원을 제공 합니다. 시각적 개체를 배포 하는 방법은 C++ 응용 프로그램을 참조 하세요 [시각적 개체에 대 한 ClickOnce 배포 C++ 응용 프로그램](/cpp/windows/clickonce-deployment-for-visual-cpp-applications)합니다.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포는 배포에서 세 가지 주요 문제를 극복 합니다.  
  
- **애플리케이션 업데이트의 어려움.** Microsoft Windows Installer 배포를 사용 하 여 응용 프로그램 업데이트 될 때마다 사용자 msp 파일을 업데이트를 설치 하는 설치 된 제품에 적용 사용 하 여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 업데이트를 자동으로 제공할 수 있습니다. 응용 프로그램의 변경 된 부분만 다운로드 하 고 전체 업데이트 된 응용 프로그램이 새 side-by-side-폴더에서 다음 다시 설치 합니다.  
  
- **사용자의 컴퓨터에 영향을 미칩니다.** Windows Installer 배포를 사용 하 여 응용 프로그램 사용 되는 버전 충돌;에 대 한 가능성을 사용 하 여 공유 구성 요소 사용 하 여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포의 경우 각 응용 프로그램은 독립적 이며 다른 응용 프로그램을 방해할 수 없습니다.  
  
- **보안 권한.** Windows Installer 배포 관리자 권한이 필요 하며 제한 된 사용자 설치만 허용 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 관리자가 아닌 사용자가 설치를 사용 하도록 설정 및 응용 프로그램에 필요한 코드 액세스 보안 권한만 부여 합니다.  
  
  과거에는 이러한 문제로 인해 개발자를 Windows 기반 응용 프로그램을 쉽게 설치에 대 한 풍부한 사용자 인터페이스를 희생 하는 대신 웹 응용 프로그램을 만들어야 합니다. 사용 하 여 배포 된 응용 프로그램을 사용 하 여 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], 두 기술의 장점을 모두 활용할 수 있습니다.  
  
## <a name="what-is-a-clickonce-application"></a>ClickOnce 응용 프로그램 이란?  
 A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램은 Windows Presentation Foundation (.xbap), Windows Forms (.exe), 콘솔 응용 프로그램 (.exe), 또는 Office 솔루션 (.dll)을 사용 하 여 게시 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 기술 합니다. 게시할 수는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 세 가지 방법으로 응용 프로그램: 웹 페이지, 네트워크 파일 공유 또는 CD-ROM 같은 미디어에서. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램을 최종 사용자의 컴퓨터에 설치 하 고 컴퓨터를 오프 라인으로 또는 영구적으로 최종 사용자의 컴퓨터에 아무것도 설치 하지 않고 온라인 전용 모드에서 실행할 수 있습니다 하는 경우에 로컬로 실행할 수 있습니다. 자세한 내용은 [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)을 참조하세요.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램 수 자동 업데이트 됩니다. 이러한 최신 버전 사용 가능 하며 자동으로 업데이트 된 파일을 바꿀으로 확인할 수 있습니다. 개발자는 업데이트 동작을 지정할 수 있으며, 네트워크 관리자는 강제 업데이트 지정과 같은 업데이트 전략을 제어할 수 있습니다. 업데이트 수 롤백할 수도 이전 버전으로 최종 사용자 또는 관리자가 있습니다. 자세한 내용은 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)을 참조하세요.  
  
 때문에 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램은 설치 또는 실행 격리는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램에는 기존 응용 프로그램 중단 될 수 없습니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램은 자체 포함 합니다. 각 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램에 설치 되 고 안전한 사용자별, 응용 프로그램별 캐시에서에서 실행 합니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램은 인터넷 또는 인트라넷 보안 영역에서 실행합니다. 필요한 경우 애플리케이션이 승격된 보안 권한을 요청할 수 있습니다. 자세한 내용은 [ClickOnce 애플리케이션 게시](../deployment/securing-clickonce-applications.md)를 참조하세요.  
  
## <a name="how-clickonce-security-works"></a>ClickOnce 보안의 작동 원리  
 핵심 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 보안은 인증서, 코드 액세스 보안 정책 및 ClickOnce 신뢰 프롬프트를 기반 합니다.  
  
### <a name="certificates"></a>인증서  
 Authenticode 인증서는 응용 프로그램의 게시자의 신뢰성을 확인 하는 데 사용 됩니다. ClickOnce 응용 프로그램 배포에 Authenticode를 사용 하 여 신뢰할 수 있는 원본에서 온 적법 한 프로그램으로에서 유해한 프로그램을 방지할 수 있습니다. 필요에 따라 응용 프로그램 서명에 인증서도 사용할 수 및 배포 매니페스트 파일이 손상 되지 않았는지를 증명 하기 위해. 자세한 내용은 [ClickOnce 및 Authenticode](../deployment/clickonce-and-authenticode.md)합니다. 인증서는 신뢰할 수 있는 게시자 목록이 클라이언트 컴퓨터를 구성 하려면 데도 사용할 수 있습니다. 응용 프로그램이 신뢰할 수 있는 게시자를 전달 하는 경우 사용자 개입 없이 설치할 수 있습니다. 자세한 내용은 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)을 참조하십시오.  
  
### <a name="code-access-security"></a>코드 액세스 보안  
 코드 액세스 보안에 보호 된 리소스에 있는 코드의 액세스를 제한 하는 데 도움이 됩니다. 대부분의 경우에서 사용 권한을 제한 하도록 인터넷 또는 로컬 인트라넷 영역을 선택할 수 있습니다. 사용 합니다 **보안** 페이지에 **ProjectDesigner** 응용 프로그램에 대 한 적절 한 영역을 요청 하려면. 또한 최종 사용자 환경을 에뮬레이트 하려면 제한 된 권한으로 응용 프로그램을 디버깅할 수 있습니다. 자세한 내용은 [ClickOnce 애플리케이션의 코드 액세스 보안](../deployment/code-access-security-for-clickonce-applications.md)을 참조하세요.  
  
### <a name="clickonce-trust-prompt"></a>ClickOnce 신뢰 프롬프트  
 영역에서 허용 하는 보다 많은 권한을 요청 하는 응용 프로그램을 하는 경우 최종 사용자 신뢰 결정을 내리는 데 묻는 수 있습니다. 최종 사용자는 ClickOnce 응용 프로그램 같은 Windows Forms 응용 프로그램, Windows Presentation Foundation 응용 프로그램, 콘솔 응용 프로그램, XAML 브라우저 응용 프로그램 및 Office 솔루션 실행 하도록 신뢰할 수 있는 경우 결정할 수 있습니다. 자세한 내용은 [방법: ClickOnce 신뢰 프롬프트 동작 구성](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)합니다.  
  
## <a name="how-clickonce-deployment-works"></a>ClickOnce 배포 작동 방식  
 핵심 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 배포 아키텍처는 기반으로 두 개의 XML 매니페스트 파일: 응용 프로그램 매니페스트 및 배포 매니페스트 합니다. 파일을 사용 하 여 ClickOnce 응용 프로그램에서 설치 되어 있는, 업데이트 하는 방법 및 업데이트할 시기에 대해 설명 합니다.  
  
### <a name="publishing-clickonce-applications"></a>ClickOnce 애플리케이션 게시  
 응용 프로그램 매니페스트는 응용 프로그램 자체를 설명합니다. 어셈블리, 종속성 및 응용 프로그램, 필요한 권한, 그리고 업데이트 사용할 수 있는 위치를 구성 하는 파일을 포함 합니다. Visual Studio 또는 매니페스트 생성 및 편집 도구 (Mage.exe)의 게시 마법사를 사용 하 여 응용 프로그램 매니페스트를 작성 하는 응용 프로그램 개발자는 [!INCLUDE[winsdklong](../includes/winsdklong-md.md)]합니다. 자세한 내용은 [방법: 게시 마법사를 사용하여 ClickOnce 애플리케이션 게시](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)를 참조하세요.  
  
 배포 매니페스트는 애플리케이션이 배포되는 방법을 기술합니다. 이 응용 프로그램 매니페스트의 위치 및 클라이언트를 실행 해야 하는 응용 프로그램의 버전을 포함 합니다.  
  
### <a name="deploying-clickonce-applications"></a>ClickOnce 응용 프로그램 배포  
 작성된 배포 매니페스트는 배포 위치에 복사됩니다. 이러한 위치는 웹 서버, 네트워크 파일 공유 또는 CD와 같은 미디어일 수 있습니다. 응용 프로그램 매니페스트와 모든 응용 프로그램 파일 배포 매니페스트에 지정 된 배포 위치에 복사 됩니다. 이 위치는 배포 위치와 동일하거나 다른 위치일 수 있습니다. 사용 하는 경우는 **게시 마법사** Visual Studio에서 복사 작업을 자동으로 수행 됩니다.  
  
### <a name="installing-clickonce-applications"></a>ClickOnce 응용 프로그램 설치  
 배포 위치로 복사한 다음에는 최종 사용자가 웹 페이지 또는 폴더에 있는 배포 매니페스트 파일의 아이콘을 클릭하여 애플리케이션을 다운로드하고 설치할 수 있습니다. 대부분의 경우에서 최종 사용자는 사용자에 게는 설치가 진행 되 고 추가 개입 없이 시작 되는 응용 프로그램 설치를 확인 하는 간단한 대화 상자를 사용 하 여 표시 됩니다. 관리자 권한 또는 응용 프로그램은 신뢰할 수 있는 인증서로 서명 되지 않은 경우 응용 프로그램에 필요한 경우에도 대화 상자 설치를 계속 하기 전에 권한을 부여 하려면 사용자에 게 요청 합니다. 그러나 ClickOnce 설치는 사용자별, 관리자 권한이 필요한 필수 구성 요소가 있는 경우에 권한 상승 필요할 수 있습니다. 권한에 대 한 자세한 내용은 참조 하세요. [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)합니다.  
  
 인증서 수 신뢰할 수 있는 컴퓨터 또는 엔터프라이즈 수준에서 신뢰할 수 있는 인증서로 서명 된 ClickOnce 응용 프로그램을 자동으로 설치할 수 있도록 합니다. 신뢰할 수 있는 인증서에 대 한 자세한 내용은 참조 하세요. [신뢰할 수 있는 응용 프로그램 배포 개요](../deployment/trusted-application-deployment-overview.md)합니다.  
  
 응용 프로그램 사용자에 추가할 수 있습니다 **시작** 메뉴 및 합니다 **프로그램 추가 / 제거** 그룹에 **제어판**. 다른 배포 기술과 달리 아무 것도 추가 합니다 **Program Files** 설치에는 폴더 또는 레지스트리 및 관리 권한이 없는 필요  
  
> [!NOTE]
> 에 추가 되 고 응용 프로그램을 방지할 수 이기도 합니다 **시작** 메뉴 및 **프로그램 추가 / 제거** 그룹, 웹 응용 프로그램 처럼 적용 하므로. 자세한 내용은 [ClickOnce 배포 전략 선택](../deployment/choosing-a-clickonce-deployment-strategy.md)을 참조하세요.  
  
### <a name="updating-clickonce-applications"></a>ClickOnce 응용 프로그램 업데이트  
 응용 프로그램 개발자가 응용 프로그램의 업데이트 된 버전을 만들 때 새 응용 프로그램 매니페스트를 생성 하며 배포 위치에 파일 복사-일반적으로 형제 폴더로 원래 응용 프로그램 배포. 관리자는 애플리케이션의 새 버전 위치를 가리키도록 배포 매니페스트를 업데이트합니다.  
  
> [!NOTE]
> 합니다 **게시 마법사** 이러한 단계를 수행 하려면 Visual Studio에서 사용할 수 있습니다.  
  
 배포 위치 외에도 배포 매니페스트에는 애플리케이션이 업데이트된 버전을 확인할 수 있는 업데이트 위치(웹 페이지 또는 네트워크 파일 공유)가 포함됩니다. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] **게시** 속성은 응용 프로그램 업데이트를 확인 하는 시기 및 빈도 지정 하는 데 사용 됩니다. 업데이트 동작은 배포 매니페스트에서 지정할 수 있습니다 또는 이용 하 여 응용 프로그램의 사용자 인터페이스에서 사용자 선택으로 제공할 수 있습니다는 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Api. 또한 **게시** 속성을 사용하여 업데이트를 강제로 수행하거나 이전 버전으로 롤백하도록 지정할 수도 있습니다. 자세한 내용은 [ClickOnce 업데이트 전략 선택](../deployment/choosing-a-clickonce-update-strategy.md)을 참조하세요.  
  
### <a name="third-party-installers"></a>타사 설치 관리자  
 응용 프로그램과 함께 타사 구성 요소를 설치 하 여 ClickOnce 설치 관리자를 사용자 지정할 수 있습니다. 재배포 가능 패키지 (.exe 또는.msi 파일)를 포함 하며 언어 중립 제품 매니페스트 및 언어별 패키지 매니페스트를 사용 하 여 패키지에 설명 합니다. 자세한 내용은 [부트스트래퍼 패키지 만들기](../deployment/creating-bootstrapper-packages.md)합니다.  
  
## <a name="clickonce-tools"></a>ClickOnce 도구  
 다음 표에서 생성, 편집, 서명 및 응용 프로그램 및 배포 매니페스트에 다시 서명할를 사용할 수 있는 도구를 보여 줍니다.  
  
|도구|설명|  
|----------|-----------------|  
|[프로젝트 디자이너, 보안 페이지](../ide/reference/security-page-project-designer.md)|응용 프로그램 및 배포 매니페스트에 서명 합니다.|  
|[프로젝트 디자이너, 게시 페이지](../ide/reference/publish-page-project-designer.md)|생성 하 고 Visual Basic 및 Visual C# 응용 프로그램에 대 한 응용 프로그램 및 배포 매니페스트를 편집 합니다.|  
|[Mage.exe(매니페스트 생성 및 편집 도구)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)|Visual Basic의 경우 시각적 개체에 대 한 응용 프로그램 및 배포 매니페스트를 생성 C#, 및 시각적 C++ 응용 프로그램입니다.<br /><br /> 서명 하 고 응용 프로그램 및 배포 매니페스트에 다시 서명 키를 누릅니다.<br /><br /> 일괄 처리 스크립트 및 명령 프롬프트에서 실행할 수 있습니다.|  
|[MageUI.exe(매니페스트 생성 및 편집 도구, 그래픽 클라이언트)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)|생성 하 고 응용 프로그램 및 배포 매니페스트를 편집 합니다.<br /><br /> 서명 하 고 응용 프로그램 및 배포 매니페스트에 다시 서명 키를 누릅니다.|  
|[GenerateApplicationManifest 작업](../msbuild/generateapplicationmanifest-task.md)|응용 프로그램 매니페스트를 생성합니다.<br /><br /> MSBuild에서 실행할 수 있습니다. 자세한 내용은 [MSBuild 참조](../msbuild/msbuild-reference.md)를 참조하세요.|  
|[GenerateDeploymentManifest 작업](../msbuild/generatedeploymentmanifest-task.md)|배포 매니페스트를 생성합니다.<br /><br /> MSBuild에서 실행할 수 있습니다. 자세한 내용은 [MSBuild 참조](../msbuild/msbuild-reference.md)를 참조하세요.|  
|[SignFile 작업](../msbuild/signfile-task.md)|응용 프로그램 및 배포 매니페스트에 서명 합니다.<br /><br /> MSBuild에서 실행할 수 있습니다. 자세한 내용은 [MSBuild 참조](../msbuild/msbuild-reference.md)를 참조하세요.|  
|<xref:Microsoft.Build.Tasks.Deployment.ManifestUtilities>|응용 프로그램 및 배포 매니페스트를 생성 하려면 사용자 고유의 응용 프로그램을 개발 합니다.|  
  
 다음 표에서 이러한 브라우저에서 ClickOnce 응용 프로그램을 지 원하는 데 필요한.NET Framework 버전을 보여 줍니다.  
  
|브라우저|.NET Framework 버전|  
|-------------|----------------------------|  
|Internet Explorer|2.0, 3.0, 3.5, 3.5 SP1, 4|  
|Firefox|2.0 SP1, 3.5 SP1, 4|  
  
## <a name="see-also"></a>참고 항목  
 [Windows Vista의 ClickOnce 배포](../deployment/clickonce-deployment-on-windows-vista.md)   
 [ClickOnce 응용 프로그램 게시](../deployment/publishing-clickonce-applications.md)   
 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)   
 [ClickOnce를 사용하여 COM 구성 요소 배포](../deployment/deploying-com-components-with-clickonce.md)   
 [명령줄에서 ClickOnce 응용 프로그램 빌드](../deployment/building-clickonce-applications-from-the-command-line.md)   
 [System.Deployment.Application을 사용하는 ClickOnce 응용 프로그램 디버그](../deployment/debugging-clickonce-applications-that-use-system-deployment-application.md)
