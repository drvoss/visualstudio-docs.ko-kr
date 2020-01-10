---
title: 프로젝트 포팅, 마이그레이션, 업그레이드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
caps.latest.revision: 108
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 0f41abab206362ea60fafa30f2abcbf5eb474ddc
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849924"
---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Visual Studio 프로젝트 포팅, 마이그레이션, 업그레이드
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에 대한 최신 설명서는 [프로젝트 마이그레이션 및 Visual Studio에 대한 업그레이드 참조](/visualstudio/porting/port-migrate-and-upgrade-visual-studio-projects)를 참조하세요.

최신 버전의 Visual Studio로 이동할지 여부를 고려 하는 경우이 문서를 사용 하 여 Visual Studio 2013, Visual Studio 2012 또는 Visual Studio 2010 s p 1에서 만든 솔루션, 프로젝트, 파일 및 기타 자산을 확인할 수 있습니다. Visual Studio 2013 및 Visual Studio 2015에서 수정 하지 않습니다. 또는 열어 놓은 Visual Studio 버전에서 지원되지 않거나 Azure SDK for.NET와 같이 SDK 또는 확장이 필요한 프로젝트를 열려고 할 때 오류 메시지가 발생한 경우 이 페이지로 이동되었을 수 있습니다.

널리 사용 되는 많은 자산은 Visual Studio 2015, Visual Studio 2013 및 두 가지 이전 버전에서 동일 하 게 동작 합니다. 예를 들어 Visual Studio 2015에서는 Visual Studio 2013 또는 Visual Studio 2012에서 만든 프로젝트를 열고 변경한 후 Visual Studio 2015에서 다시 열 수 있습니다. 변경 내용이 유지 되 고 프로젝트는 이전 버전과 동일 하 게 동작 합니다. Visual Studio 2010 SP1에서 만든 여러 자산의 경우에도 마찬가지입니다.

Visual Basic에서 Visual Studio 2015는 Visual Studio 2013에서 만든 Visual Basic 앱을 컴파일하지 못하도록 하는 변경 사항을 도입 하지 않았습니다. Visual Studio 2015을 사용 하 여 다시 컴파일되는 Visual Basic 앱의 런타임 동작은 변경 되지 않습니다.

Visual Studio 2013, Visual Studio 2012 또는 Visual Studio 2010 SP1과 함께 Visual Studio 2015를 사용하는 경우, 모든 버전에서 프로젝트와 파일을 만들고 수정할 수 있습니다. 하나 이상의 버전에서 지원 되지 않는 기능을 추가 하지 않는 한 버전 간에 프로젝트와 파일을 전송할 수 있습니다.

## <a name="project"></a> 프로젝트

다음 목록에서는 visual studio 2012 또는 Visual Studio 2010 s p 1에서 만든 프로젝트에 대 한 Visual Studio 2015 및 Visual Studio 2013 지원에 대해 설명 합니다. 이 목록을 사용 하 여 Visual Studio 2015, Visual Studio 2013, Visual Studio 2012 또는 Visual Studio 2010 s p 1에서 프로젝트를 "있는 그대로" 열 수 있는지 또는 호환성을 보장 하기 위해 수정 해야 하는지 여부를 결정할 수 있습니다.

|프로젝트 형식|호환성|
|---------------------|-------------------|
|유니버설 Windows 플랫폼 앱|유니버설 Windows 앱 도구를 설치하려면 Visual Studio 설치 프로그램에서 **사용자 지정** 또는 **수정**을 선택한 다음 **유니버설 Windows 앱 개발 도구**를 선택합니다.<br /><br /> Windows 10 용 UWP (유니버설 Windows 플랫폼) 앱 개발은 Windows 10 또는 [!INCLUDE[win81](../includes/win81-md.md)]의 Visual Studio 2015 에서만 지원 됩니다.|
|Windows 스토어 응용 프로그램|Windows 8.1 및 Windows Phone 8.1을 대상으로 하는 유니버설 앱을 포함한 Windows 스토어 앱 개발은 [!INCLUDE[win81](../includes/win81-md.md)] 및 Windows 10에서 지원됩니다. 기존 [!INCLUDE[win8](../includes/win8-md.md)] 프로젝트에 대한 서비스가 계속 제공되지만 새로운 [!INCLUDE[win8](../includes/win8-md.md)] 프로젝트를 만들 수는 없습니다. [!INCLUDE[win81](../includes/win81-md.md)] 프로젝트는 특정 참조 형식에 따라서만 결정됩니다. 자세한 내용은 [프로젝트의 참조 관리](../ide/managing-references-in-a-project.md)를 참조하세요. **참고:** visual studio 2015 또는 Visual Studio 2013를 사용 하 여 만든[!INCLUDE[win81](../includes/win81-md.md)] 프로젝트는 visual studio 2012에서 열 수 없습니다. 그 이유는 Visual Studio 2015을 사용 하 여 만든 프로젝트와 이러한 버전을 대상으로 하는 Visual Studio 2013 [!INCLUDE[win81](../includes/win81-md.md)] Visual Studio 2012은 [!INCLUDE[win8](../includes/win8-md.md)]를 대상으로 하는 [!INCLUDE[win8](../includes/win8-md.md)] 프로젝트만 지원 하기 때문입니다.|
|[!INCLUDE[net_v451](../includes/net-v451-md.md)]|적절 한 다중 대상 지정 팩을 설치한 후 Visual Studio 2015 및 Visual Studio 2013에서 이러한 프로젝트를 만들고 사용할 수 있습니다. Visual Studio 2010 SP1에서는 이 프로젝트가 지원되지 않습니다.|
|[!INCLUDE[net_v45](../includes/net-v45-md.md)]|Visual studio 2015, Visual Studio 2013 및 visual studio 2012에서 이러한 프로젝트를 만들고 열 수 있지만 Visual Studio 2010 s p 1에서는 만들 수 없습니다.|
|BizTalk|BizTalk server 프로젝트는 Visual Studio 2015 또는 Visual Studio 2013와 호환 되지 않습니다.|
|C#/Visual Basic Silverlight 4 애플리케이션 또는 클래스 라이브러리|Visual Studio에서 프로젝트를 자동으로 업데이트 하도록 허용 하는 경우 Visual Studio 2013 또는 Visual Studio 2012에서 프로젝트를 열 수 있습니다.|
|C#/Visual Basic Webform 또는 Windows Form|Visual Studio 2013 및 Visual Studio 2012에서 프로젝트를 열 수 있습니다.|
|Visual Basic 6 및 Visual C++ 6|Visual Studio 2012 및 Visual Studio 2013는 Visual Basic 6 또는 Visual C++ 6으로 빌드된 응용 프로그램의 디버깅을 지원 하지 않습니다. 이러한 응용 프로그램을 디버깅 하려면 이전 버전의 Visual Studio를 사용 합니다.|
|코딩된 UI 테스트|Visual Studio에서 프로젝트를 자동으로 업데이트 하도록 허용 하는 경우 Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1에서 프로젝트를 열 수 있습니다.|
|F#|Visual studio 2010 s p 1에서 만든 프로젝트를 visual Studio에서 업그레이드 하도록 허용 하는 경우 Visual Studio 2013 및 Visual Studio 2012에서 열 수 있습니다. 그러나 이전 버전의 Visual Studio에서 만든 Silverlight 프로젝트를 Visual Studio 2013로 업그레이드할 수는 없습니다. 대신 Visual Studio 2013에서 Silverlight 프로젝트를 만든 다음 코드를 복사 해야 합니다. 에서 만든 silverlight 프로젝트는 Silverlight 5 Visual Studio 2013 대상으로 합니다.|
|LightSwitch|Visual Studio에서 프로젝트를 자동으로 업그레이드 하도록 허용 하는 경우 Visual Studio 2013 에서만 열 수 있습니다.|
|로컬 데이터베이스 캐시|로컬 데이터베이스 캐시 템플릿과 **데이터 동기화 구성** 대화 상자는 Visual Studio 2013에 포함 되어 있지 않습니다. Microsoft Synchronization Services v 1.0이 설치 된 경우 Visual Studio 2013를 사용 하 여 [!INCLUDE[vs2010](../includes/vs2010-md.md)]에서 만든 프로젝트를 열고 실행할 수 있지만 Visual Studio 2013에서 업데이트 하려면 코드에서 모든 항목을 수동으로 변경 해야 합니다. 또는 [!INCLUDE[vs2010](../includes/vs2010-md.md)] 을 계속 사용하여 이 프로젝트를 유지하고 업데이트할 수 있습니다.  새로운 개발의 경우 Microsoft Sync Framework에서 제공하는 새로운 동기화 모델을 대상으로 합니다. 자세한 내용은 [Microsoft Sync Framework 개발자 센터](https://msdn.microsoft.com/sync/default)를 참조하세요.|
|모델-뷰-컨트롤러 프레임워크|Visual Studio 2010 s p 1은 MVC 2 및 MVC 3만 지원 하 고 Visual Studio 2012은 mvc 3 및 MVC 4만 지원 하며 Visual Studio 2013는 MVC 4만 지원 합니다. MVC 2에서 MCV 3로 자동 업그레이드하는 방법에 대한 자세한 내용은 [ASP.NET MVC 3 애플리케이션 업그레이더](https://aspnet.codeplex.com/releases/view/59008)를 참조하세요. MVC 2에서 MVC 3로 수동 업그레이드하는 방법에 대한 자세한 내용은 [ASP.NET MVC 3 도구 업데이트로 ASP.NET MVC 2 프로젝트 업그레이드](https://aspnet.codeplex.com/releases/view/59008)를 참조하세요. MVC 3에서 MVC 4로 수동 업그레이드하는 방법에 대한 자세한 내용은 [ASP.NET MVC 3 프로젝트를 ASP.NET MVC 4로 업그레이드](https://docs.microsoft.com/aspnet/whitepapers/mvc4-release-notes)를 참조하세요. 프로젝트 대상이 .NET Framework 3.5 SP1일 경우 대상을 변경하여 .NET Framework 4를 사용해야 합니다.|
|모델링|Visual Studio에서 프로젝트를 자동으로 업데이트하도록 허용하면 Visual Studio 2013, Visual Studio 2012 또는 Visual Studio 2010 SP1에서 프로젝트를 열 수 있습니다.<br /><br /> Team Foundation에서 모델링 프로젝트를 빌드할 때 프로젝트의 레이어 유효성 검사를 시도합니다. Visual Studio 2013 Team Foundation Build는 Visual Studio 2010 s p 1에서 만든 모델링 프로젝트의 레이어 유효성을 검사할 수 없습니다. 그러나 Visual Studio 2010 s p 1에서는 Team Foundation Build가 Visual Studio 2013에서 만든 모델링 프로젝트의 레이어 유효성을 검사할 수 있습니다.|
|MPI/클러스터 디버깅|Visual Studio 2013, Visual Studio 2012 또는 Visual Studio 2010 s p 1을 실행 하는 컴퓨터에 같은 버전의 런타임 또는 도구가 설치 되어 있으면 세 버전 모두에서이 프로젝트를 열 수 있습니다.|
|MSI 설치(.vdproj)|이 프로젝트는 해당 프로젝트 형식을 지원 하지 않으므로 Visual Studio 2013에서 열 수 없습니다. 대부분의 Windows 플랫폼과 애플리케이션 런타임을 직접 지원하는 무료 배포 솔루션인 ISLE(InstallShield Limited Edition for Visual Studio)를 사용하는 것이 좋습니다. ISLE를 사용하여 Visual Studio 설치 관리자 프로젝트에서 데이터 및 설정을 가져올 수도 있습니다. 에서 수정하지 않아도 실행되는 항목을 찾을 수 있습니다.|
|Office 2007 VSTO|Office 2013 및 .NET Framework 4를 대상으로 하는 프로젝트를 업그레이드 하는 경우 Visual Studio 2013, Visual Studio 2012 또는 Visual Studio 2010 s p 1에서이 프로젝트를 열 수 있습니다.|
|Office 2010 VSTO|프로젝트가 .NET Framework 4를 대상으로 하는 경우 Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1에서 열 수 있습니다. 다른 모든 프로젝트에는 단방향 업그레이드가 필요합니다.|
|리치 인터넷 애플리케이션|프로젝트를 업그레이드 하는 경우 Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1에서 프로젝트를 열 수 있습니다.|
|SharePoint 2007|Visual Studio 2013에서이 프로젝트를 열 수 없습니다. 그러나 프로젝트를 수동으로 SharePoint 2010로 업그레이드 하는 경우 Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1에서이 프로젝트를 열 수 있습니다. SharePoint 2007을 업그레이드하는 방법은 [SharePoint 2007에서 SharePoint 2010으로 마이그레이션(IT 전문가용)](https://channel9.msdn.com/Blogs/matthijs/Migrating-from-SharePoint-2007-to-SharePoint-2010-for-the-IT-Pro) 및 [SharePoint Server 2010용 SharePoint Enterprise 검색 마이그레이션 도구](https://docs.microsoft.com/previous-versions/office/developer/sharepoint-2010/ee556856(v%3Doffice.14))를 참조하세요.|
|SharePoint 2010|Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1에서 프로젝트를 열 수 있습니다.|
|SketchFlow|Visual Studio에서 프로젝트를 WPF 4.5/Silverlight 5로 업그레이드할 수 있도록 허용 하는 경우 Visual Studio 2012 및 Visual Studio 2013에서 프로젝트를 열 수 있습니다.|
|[!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)] 데이터베이스|Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1에서 프로젝트를 열 수 있습니다. 이전 버전의 SQL Server에서 만든 데이터베이스 파일(.mdf)이 있을 경우 SQL Server Express LocalDB에서 이 데이터베이스 파일을 사용하려면 먼저 [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] 로 업그레이드해야 합니다. 하지만 데이터베이스가 더 이상 이전 버전의 SQL Server와 호환되지 않습니다. 업그레이드 하지 않는 경우 동일한 컴퓨터에 [!INCLUDE[ssKatmai_exp](../includes/sskatmai-exp-md.md)]를 설치 하 고 사용 하 여 Visual Studio 2013에서 데이터베이스 작업을 계속할 수 있습니다. 자세한 내용은 [.mdf 파일 업그레이드](../data-tools/upgrade-dot-mdf-files.md)를 참조하세요.|
|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express|[!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] Express가 Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1을 실행 하는 컴퓨터에 설치 된 경우 세 버전 모두에서 프로젝트를 열 수 있습니다.|
|SQL Server 보고서 프로젝트|Visual Studio 2013 및 Visual Studio 2012에서 프로젝트를 열 수 있습니다. 로컬 모드에서만(즉, SQL Server에 연결되어 있지 않은 경우) [!INCLUDE[vs2010](../includes/vs2010-md.md)]의 뷰어와 연결된 컨트롤에 대해 디자인 타임 환경을 가져올 수 없습니다. 하지만 프로젝트는 런타임에 올바르게 작동합니다. **주의:**  Visual Studio 2013와 관련 된 기능을 추가 하는 경우 보고서 스키마가 자동으로 업그레이드 되 고 Visual Studio 2012에서 더 이상 프로젝트를 열 수 없습니다.|
|단위 테스트|Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1에서 [!INCLUDE[TCMext](../includes/tcmext-md.md)]를 사용 하 여 이러한 버전에서 만든 테스트를 열 수 있습니다.|
|Visual C++|Visual Studio 2013를 사용 하 여 Visual Studio C++ 2012 또는 visual studio 2010 s p 1에서 만든 프로젝트를 열 수 있습니다. Visual Studio 2013 빌드 환경을 사용 하 여 Visual Studio 2012에서 만든 프로젝트를 빌드하려면 같은 컴퓨터에 두 버전의 Visual Studio가 모두 설치 되어 있어야 합니다. 자세한 내용은 [방법: Visual C++ 프로젝트를 Visual Studio 2015로 업그레이드](../porting/how-to-upgrade-visual-cpp-projects-to-visual-studio-2015.md) 및 [Visual C++ 포팅 및 업그레이드 가이드](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb)를 참조하세요.|
|Visual Studio 2010 웹|Visual Studio에서 프로젝트를 자동으로 업그레이드 하도록 허용 하는 경우 Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1에서 프로젝트를 열 수 있습니다.|
|Visual Studio 2010 데이터베이스(.dbproj)|프로젝트를 SQL Server Data Tools 데이터베이스 프로젝트로 변환 하는 경우 Visual Studio 2013에서 열 수 있습니다. 그러나 Visual Studio 2013은 이러한 아티팩트를 지원 하지 않습니다.<br /><br /> -   단위 테스트<br />-   데이터 생성 계획<br />-   데이터 비교 파일<br />-   정적 코드 분석을 위한 사용자 지정 규칙 확장명<br />-   server.sqlsettings<br />-   .sqlcmd 파일<br />-   사용자 지정 배포 확장명<br />-   부분 프로젝트(.files)<br /><br /> SQL Server 데이터 도구를 설치할 경우 변환 후에 Visual Studio 2010 SP1에서 프로젝트를 열 수 있습니다. 자세한 내용은 [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx)를 참조하세요.|
|Visual Studio 2010 Visual Database Tools|Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 SP1에서 이 프로젝트를 열 수 있습니다.|
|Visual Studio Lab Management|[!INCLUDE[TCMext](../includes/tcmext-md.md)], Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1을 사용 하 여 이러한 버전에서 만든 환경을 열 수 있습니다. 그러나 환경을 만들기 전에 Microsoft Test Manager 버전이 Team Foundation Server 버전과 일치해야 합니다.|
|Visual Studio 매크로|프로젝트 형식을 지원 하지 않으므로 Visual Studio 2013에서이 프로젝트를 열 수 없습니다.|
|Visual Studio SDK/VSIX|Visual Studio SDK 프로젝트를 Visual Studio 2013로 업그레이드 한 후에는 Visual Studio 2012에서 열 수 없습니다. 자세한 내용은 [방법: Visual Studio 2015로 확장성 프로젝트 마이그레이션](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)을 참조하세요.|
|Visual Studio용 Microsoft Azure 도구|Visual Studio 버전 2.1에 Microsoft Azure 도구를 사용 하는 경우 Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1에서 프로젝트를 열 수 있습니다. 이전 버전을 대상으로 하는 프로젝트의 경우 Visual Studio에서 프로젝트를 버전 2.1로 업그레이드 하도록 허용 하면 Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 s p 1에서 프로젝트를 열 수 있습니다.|
|Windows Communication Foundation, Windows Presentation Foundation|Visual Studio 2013, Visual Studio 2012 및 Visual Studio 2010 SP1에서 이 프로젝트를 열 수 있습니다.|
|Windows Mobile|프로젝트 형식을 지원 하지 않으므로 Visual Studio 2013에서이 프로젝트를 열 수 없습니다.|
|Windows Phone 7.1|Visual Studio에서 프로젝트를 Windows Phone 8.0로 업그레이드 하도록 허용 하는 경우 Visual Studio 2012 및 Visual Studio 2013에서 프로젝트를 열 수 있습니다.|
|기타|Visual Studio 2012, Visual Studio 2013 및 Visual Studio 2010 s p 1에서 대부분의 다른 프로젝트 형식을 열 수 있습니다.|
|FrontPage 웹 사이트|프로젝트 형식을 지원 하지 않으므로 Visual Studio 2013에서이 프로젝트를 열 수 없습니다.|
|이식 가능한 클래스 라이브러리|Visual Studio에서 프로젝트를 자동으로 업데이트하도록 허용하면 Visual Studio 2013, Visual Studio 2012 또는 Visual Studio 2010 SP1에서 프로젝트를 열 수 있습니다.<br /><br /> -   Silverlight 4를 대상으로 하는 프로젝트는 Silverlight 5를 대상으로 합니다.<br />-   Windows Phone 7.0 또는 Windows Phone 7.5를 대상으로 하는 프로젝트는 Windows Phone 8을 대상으로 합니다.<br />-   Xbox 360을 대상으로 하던 프로젝트가 더 이상 Xbox 360을 대상으로 하지 않습니다.|
|클라우드 서비스 프로젝트와 같은 Azure 프로젝트(확장명 .ccproj) 및 Azure 리소스 관리자 프로젝트(클라우드 배포 프로젝트)(확장명 .deployproj)|이러한 형식의 프로젝트를 열려면 먼저 [Azure SDK for.NET](https://azure.microsoft.com/downloads/)을 설치한 다음 프로젝트를 엽니다.|

## <a name="troubleshooting-project-compatibility-issues"></a>프로젝트 호환성 문제 해결
 Visual Studio 2015 또는 Visual Studio 2013에서 프로젝트가 열리지 않을 경우 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- Visual Studio 2015 또는 Visual Studio 2013에서 지원 되지 않고 연결 된 Visual Studio 버전이 설치 되지 않은 프로젝트를 열려고 하면 프로젝트 형식이 지원 되지 않는다는 메시지가 표시 되 고 **지원 되지 않는**프로젝트의 프로젝트 **및 솔루션 변경 내용 검토** 대화 상자에 프로젝트 형식이 나열 될 수 있습니다. 이 문제를 해결하려면 Windows **제어판**에서 프로그램 및 기능 페이지를 열고 **Visual Studio**를 선택한 다음 **변경**, **복구**를 차례로 선택합니다. 그러면 누락된 버전을 설치할 수 있습니다.

- [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]에서 데스크톱 앱의 프로젝트를 열려고 하면 오류가 발생하고 다음 메시지 중 하나가 표시됩니다. "이 버전의 Visual Studio는 [!INCLUDE[win81](../includes/win81-md.md)] 앱만 지원합니다." 또는 "이 프로젝트는 현재 버전의 Visual Studio와 호환되지 않습니다." [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]는 Windows 8.1용으로 설계된 Windows 스토어 앱을 개발하고 테스팅하며 배포하는 것으로 제한됩니다. 데스크톱 응용 프로그램 프로젝트를 열려면 해당 프로젝트 형식을 지원하는 Visual Studio의 버전을 사용해야 합니다.

   Visual Studio 버전에 대한 자세한 내용은 [Microsoft Visual Studio 제품](https://visualstudio.microsoft.com/products/)을 참조하세요.

- [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop에서 Windows 스토어 앱 프로젝트를 열려고 시도하면 오류가 발생합니다. [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)] Desktop을 사용하여 Windows 스토어 앱을 빌드할 수 없습니다. Windows 스토어 앱을 빌드하려는 경우 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]도 설치할 수 있습니다. 또는 모든 Microsoft 플랫폼 및 웹 응용 프로그램을 개발하려면 Visual Studio Professional 2013을 사용해 보세요.

- 프로젝트에 Visual Studio 2013 관련 된 기능이 필요한 경우 이전 버전에서 열 수 없습니다.

- Visual Studio 2012을 사용 하는 경우 Visual Studio 2013에서 만든 프로젝트를 열려면 프로젝트 시스템을 사용자 지정 하 여 Visual Studio 2013 기능을 통합할 수 있습니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 [사용자 지정 프로젝트의 버전 인식 설정](../misc/making-custom-projects-version-aware.md)을 참조하세요.

  추가 문제 해결 방법을 보려면 [Visual Studio 2013 호환성](https://support.microsoft.com/help/2863286/roundtrip-issues-for-visual-studio-2012-and-visual-studio-2013-preview) KB 문서를 참조하세요.

## <a name="file"></a> 파일

다음 목록에서는 Visual Studio 2013에서 각 파일 형식을 지원 하는지 여부, Visual Studio 2012 및 Visual Studio 2010 s p 1에서 파일을 열 수 있는지 여부 및 호환성을 보장 하기 위해 수정 해야 하는지 여부를 식별 합니다.

|파일 형식|호환성|
|------------------|-------------------|
|AppManifest, Inbrowsersettings, OutOfBrowserSettings(.xml 파일)|이러한 파일은 Visual Studio 2012, Visual Studio 2013 및 Visual Studio 2010 s p 1에서 열 수 있습니다.|
|BizTalk 플랫 파일 스키마|Visual Studio 2013에서 BizTalk 2013 프로젝트에 이러한 스키마를 추가할 수 있습니다. 플랫 파일 스키마가 있는 BizTalk 2010 프로젝트에 Visual Studio 2013을 사용 하려면 Visual Studio 2013 있는 컴퓨터에 BizTalk 2013을 설치 합니다. BizTalk 2010 프로젝트를 처음 열 때 BizTalk 2013 또는 Visual Studio 2013 프로젝트 시스템으로 자동 업그레이드 됩니다.|
|클라이언트 보고서 정의(.rdlc) 파일|이러한 파일은 Visual Studio 2013에서 열 수 있으며 Visual Studio 2013 기능 및 컨트롤을 추가 하는 경우 스키마가 자동으로 업그레이드 됩니다.|
|코드 분석 규칙 집합|이러한 파일은 Visual Studio 2012, Visual Studio 2013 및 Visual Studio 2010 s p 1에서 열 수 있습니다.|
|데이터 계층 애플리케이션 패키지 파일|이러한 파일은 버전 2.0 또는 버전 2.5 인 경우 Visual Studio 2013에서 열 수 있습니다.|
|디버거 덤프 파일|이러한 파일은 Visual Studio 2012, Visual Studio 2013 및 Visual Studio 2010 s p 1에서 열 수 있습니다.|
|DGML(Directed Graph Markup Language) 다이어그램 파일|파일을 변경 하지 않고 Visual Studio 2012, Visual Studio 2013 및 Visual Studio 2010 s p 1에서 이러한 파일을 열 수 있습니다.|
|EDMX(엔터티 데이터 모델) 파일|Visual Studio 2013에서 파일을 변경 하지 않고 .NET Framework 4.5 또는 .NET Framework 4를 대상으로 하는 EDMX 파일을 열 수 있습니다.|
|프로파일러 보고서 파일|Visual Studio 2012 및 Visual Studio 2013에서 프로파일러 보고서 파일 (.vsp. .vsps,. .psess 및. .vspf)을 열 수 있습니다. Visual Studio 2010 SP1에서는 .vspx 파일을 열 수 없습니다.|
|솔루션(.suo) 파일|Visual Studio 2013를 사용 하 여 Visual Studio 2012 또는 Visual Studio 2010 s p 1에서 만든 솔루션 파일을 열 수 있습니다.|
|SQL Server Compact Edition|Visual Studio 2013 SQL Server Compact 버전을 지원 하지 않습니다.|
|SQLX 파일|Visual Studio 2013에서 이러한 파일을 열려면 단방향 업그레이드를 수행 하 고, 대상 버전의 Visual Studio에. sqlx 파일을 배포한 후 .dacpac 형식으로 파일을 다시 작성 해야 합니다.|
|[!INCLUDE[vs2010](../includes/vs2010-md.md)]의 IntelliTrace 로그 파일|이러한 파일은 Visual Studio 2012, Visual Studio 2013 및 Visual Studio 2010 s p 1에서 열 수 있습니다.|
|JavaScript 메모리 분석기(.diagsession) 파일|이전 버전의 Visual Studio에서 만든 파일은 Visual Studio 2013에서 볼 수 있습니다. 그러나 수집 된 정보에 따라 Visual Studio 2013에서 만든 파일은 Visual Studio 2012 또는 Visual Studio 2010 s p 1에서 열리지 않을 수 있습니다.|

## <a name="integration"></a> 통합 자산

여러 버전의 Visual Studio Team Foundation Server의 클라이언트와 서버를 사용하는 경우 호환성 문제가 발생할 수 있습니다.

|통합의 종류|호환성|
|-------------------------|-------------------|
|코드 검토 및 내 작업|[!INCLUDE[esprfound](../includes/esprfound-md.md)] 의 클라이언트를 [!INCLUDE[vstsTfsRosarioLong](../includes/vststfsrosariolong-md.md)]에 연결하는 경우 코드 검토 및 내 작업 기능을 사용할 수 없습니다.|
|[!INCLUDE[vs_dev11_expwin_long](../includes/vs-dev11-expwin-long-md.md)]|MSBuild 또는 [!INCLUDE[esprbuild](../includes/esprbuild-md.md)] 같은 64비트 환경을 사용하여 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 에서 만든 [!INCLUDE[vs_dev12_expwin](../includes/vs-dev12-expwin-md.md)]앱을 빌드할 수 없습니다.|

## <a name="see-also"></a>참조

- [사용자 지정 프로젝트의 버전 인식 설정](../misc/making-custom-projects-version-aware.md)
