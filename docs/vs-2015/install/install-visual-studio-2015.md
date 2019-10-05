---
title: Visual Studio 2015 설치 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- vs.about
helpviewer_keywords:
- Visual Studio, installing
- installing Visual Studio
- server installations [Visual Studio]
- Setup [Visual Studio]
- install Visual Studio
- visual studio installer
ms.assetid: da049020-cfda-40d7-8ff4-7492772b620f
caps.latest.revision: 183
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 677a72f0378c62f2ca65515ec563069f22b9ff09
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433020"
---
# <a name="install-visual-studio-2015"></a>Visual Studio 2015 설치

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 페이지에는 개발자를 위한 통합 생산성 도구 제품군인 **Visual Studio 2015** 설치를 돕기 위한 자세한 정보가 포함되어 있습니다. [기능](https://www.visualstudio.com/news/vs2015-vs.aspx), [버전](http://go.microsoft.com/fwlink/?LinkID=242142), [시스템 요구 사항](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs), [다운로드](http://go.microsoft.com/fwlink/?LinkId=517106)등에 대한 정보에 빠르게 액세스할 수 있는 링크도 포함되어 있습니다.

## <a name="quick-links"></a>빠른 링크

자세한 내용을 읽기 전에 자주 요청된 링크 목록을 확인하세요.

|||
|------------------|----------------|
|![Visual Studio 다운로드](../install/media/downloads.png "다운로드") |**다운로드**: Visual Studio 2015를 설치 하려면에서 제품 실행 파일을 다운로드할 수 있습니다 합니다 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) (구독 필수), 페이지 또는 boxed 제품의 설치 미디어를 사용 합니다. [현재 또는 이전 버전의 Visual Studio를 다운로드 하는 방법에 자세히 알아보려면](https://www.visualstudio.com/vs/older-downloads/)합니다.|
|![기능에 자세히 알아보려면](../install/media/features.png "기능") |**기능**: Visual Studio 2015의 기능에 대 한 자세한 내용은 릴리스 정보 참조 [RTM](https://www.visualstudio.com/news/vs2015-vs)를 [업데이트 1](https://www.visualstudio.com/news/vs2015-update1-vs)를 [업데이트 2](https://www.visualstudio.com/news/vs2015-update2-vs), 및 [업데이트 3](https://www.visualstudio.com/news/releasenotes/vs2015-update3-vs)합니다.|
|![각 SKU에 포함 된 내용 알아보십시오](../install/media/sku.png "Sku") |**SKU**: Visual Studio 2015의 각 버전에서 사용할 수 있는 항목을 확인하려면 [Visual Studio 제품 비교](http://go.microsoft.com/fwlink/?LinkID=242142) 페이지를 참조하세요.|
|![시스템 요구 사항을 보려면](../install/media/system-requirements.png "시스템 요구 사항") |**시스템 요구 사항**: Visual Studio 2015의 각 버전에 대한 시스템 요구 사항을 보려면 [Visual Studio 2015 호환성](https://www.visualstudio.com/products/visual-studio-2015-compatibility-vs) 페이지를 참조하세요.|
|![제품 키를 찾습니다](../install/media/product-keys.png "제품 키") |**제품 키**: 제품 키를 찾으려면 참조는 [방법: Visual Studio 제품 키 찾기](../install/how-to-locate-the-visual-studio-product-key.md) 항목입니다.|
|![라이선스에 대해 알아봅니다](../install/media/licensing.png "라이선스") |**라이선싱**: 개인 고객과 기업 고객 모두에 대한 라이선싱 옵션을 확인하려면 [Visual Studio 및 MSDN 라이선싱](https://www.microsoft.com/download/details.aspx?id=13350) 백서를 참조하세요.|

## <a name="custom"></a> 기본 설치 및 사용자 지정 설치
 Visual Studio 2015를 설치할 때 매일 사용하는 구성 요소를 포함하거나 제외할 수 있습니다. 즉, 기본 설치가 사용자 지정 설치보다 더 작고 더 빠르게 설치되는 경우가 많습니다. 이전 버전에서는 기본적으로 설치된 많은 구성 요소가 이제는 이 버전에서 명시적으로 선택해야 하는 사용자 지정 구성 요소로 간주된다는 의미이기도 합니다.

 ![Visual Studio 2015 설치 대화 상자](../ide/media/vs2015-setup-screen.png "VS2015_Setup_screen")

 사용자 지정 구성 요소에는 Visual C++, Visual F#, SQL Server Data Tools, 플랫폼 간 모바일 도구 및 SDK, 타사 SDK 및 확장이 있습니다. 초기 설치 작업 동안 선택하지 않는 경우 나중에 사용자 지정 구성 요소 중에서 설치할 수 있습니다.

> [!NOTE]
> 사용자 지정 설치는 자동으로 기본 설치에 있는 구성 요소를 포함합니다.

 사용자 지정 구성 요소 전체 목록은 다음과 같습니다.

|기능 집합|구성 요소|
|------------------|----------------|
|**Updates**|Visual Studio 2015 업데이트 3|
|**프로그래밍 언어**|Visual C++<br />Visual F#<br />Python Tools for Visual Studio|
|**Windows 및 웹 개발**|ClickOnce 게시 도구<br />LightSwitch<br />Microsoft Office 개발자 도구<br />Microsoft SQL Server Data Tools<br /> Microsoft Web Developer Tools<br />Visual Studio 용 PowerShell 도구 (타사)<br />Silverlight 개발 키트<br />유니버설 Windows 앱 개발 도구<br />Windows 10 도구 및 SDK<br />Windows 8.1 및 Windows Phone 8.0/8.1 도구<br />Windows 8.1 도구 및 SDK|
|**플랫폼 간 모바일 개발**|C#/.NET(Xamarin)<br />HTML/JavaScript(Apache Cordova)<br />iOS/Android용 Visual C++ 모바일 개발<br />Clang with Microsoft CodeGen|
|**일반적인 도구와 소프트웨어 개발 키트**|Android Native Development Kit (타사)<br /> Android SDK [타사]<br />Android SDK 설치 Api (타사)<br />Apache Ant (타사)<br /> Java SE Development Kit (타사)<br /> Joyent Node.js (타사)|
|**일반 도구**|Windows 용 Git (타사)<br />Visual Studio 용 GitHub 확장 (타사)<br /> Visual Studio 확장성 도구|

## <a name="installing"></a> Visual Studio 설치
 설치 미디어 (Dvd)를 사용 하 여 Visual Studio에서 Visual Studio 구독 서비스를 사용 하 여 설치할 수는 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) 에서 웹 설치 관리자를 다운로드 하 여 웹 사이트는 [Visual Studio 다운로드](http://go.microsoft.com/fwlink/?LinkId=517106) 웹 사이트 또는 오프 라인 설치 레이아웃을 만들어 (참조를 [오프 라인 설치의 Visual Studio 만들기](../install/create-an-offline-installation-of-visual-studio.md) 페이지에 대 한 자세한).

> [!IMPORTANT]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 설치하려면 관리자 자격 증명이 필요합니다. 그러나 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 를 설치한 후에는 자격 증명이 없어도 사용에 지장이 없습니다.

 Visual Studio의 모든 요소를 설치하려면 로컬 관리자 계정이 다음 권한을 사용할 수 있어야 합니다.

|로컬 정책 개체 표시 이름|사용자 권한|
|--------------------------------------|----------------|
|백업 파일 및 디렉터리|SeBackupPrivilege|
|프로그램 디버그|SeDebugPrivilege|
|감사 및 보안 로그 관리|SeSecurityPrivilege|

 이 로컬 관리자 계정 요구 사항에 대한 자세한 내용은 기술 자료 문서 [설치 계정에 특정 사용자 권한이 없는 경우 SQL Server 설치가 실패함](https://support.microsoft.com/kb/2000257)을 참조하세요.

### <a name="BKMK_Media"></a> 설치 미디어를 사용 하 여
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 설치하려면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 설치 미디어의 루트 디렉터리에서 원하는 버전에 대한 설치 파일을 실행합니다.

|버전|설치 파일|
|-------------|-----------------------|
|Visual Studio Enterprise|vs_enterprise.exe|
|Visual Studio Professional|vs_professional.exe|
|Visual Studio 커뮤니티|vs_community.exe|

### <a name="BKMK_Website"></a> 제품 웹 사이트에서 다운로드
 방문 합니다 [Visual Studio 다운로드](http://go.microsoft.com/fwlink/?LinkId=517106) 페이지 및 원하는 Visual Studio의 버전을 선택 합니다.

### <a name="downloading-from-your-subscription-service"></a>구독 서비스에서 다운로드
 방문 합니다 [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015) 페이지 및 원하는 Visual Studio의 버전을 선택 합니다.

### <a name="BKMK_Offline"></a> 오프 라인 설치 레이아웃 만들기
 없는 경우는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 하거나 설치 미디어에서 Visual Studio 구독을 없거나 설치 하지 않으려는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 웹 설치 관리자를 사용 하 여 오프 라인으로 만들어 "연결이 끊긴된 된" 설치를 수행할 수 있습니다 설치 레이아웃입니다. 자세한 내용은 참조는 [오프 라인 설치의 Visual Studio 만들기](../install/create-an-offline-installation-of-visual-studio.md) 페이지.

## <a name="enterprise"></a> Visual Studio의 엔터프라이즈 배포
 배포 하는 방법에 대 한 자세한 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 네트워크를 통해 참조를 [Visual Studio 관리자 가이드](../install/visual-studio-administrator-guide.md)합니다.

### <a name="BKMK_Virtualized"></a> 가상화 된 환경에서 Visual Studio 설치
 **Hyper-V 비디오 문제**

 Hyper-V를 사용하도록 설정된 Windows Server 2008 R2와 가속 그래픽 어댑터를 실행하는 경우 시스템 성능이 떨어질 수 있습니다.

 자세한 내용은 Microsoft 웹 사이트의 다음 페이지를 참조 합니다. [Windows Server 2008 경우 비디오 성능이 저하 될 수 또는 Windows Server 2008 R2 기반 컴퓨터에는 Hyper-v 역할이 활성화 되어 있고 가속화 디스플레이 어댑터가 설치](http://go.microsoft.com/fwlink/?LinkID=231084)합니다.

 **Hyper-V를 사용한 디바이스 에뮬레이션**

 가상화 없이 실제 하드웨어에서 Visual Studio 2015를 설치하는 경우 Hyper-V를 사용하여 Windows 및 Android 디바이스를 에뮬레이트할 수 있게 해주는 기능을 선택할 수 있습니다. Hyper-V에 설치하는 경우에는 Windows 또는 Android 디바이스를 에뮬레이트할 수 없습니다. 이는 에뮬레이터 자체가 가상 컴퓨터이기 때문이므로 현재 VM을 다른 VM 내부에 호스트할 수는 없습니다. 해결 방법은 직접 애플리케이션을 배포 및 디버그할 수 있는 실제 Windows 또는 Android 디바이스를 보유하는 것입니다.

## <a name="optionalComponents"></a> 선택적 구성 요소 설치
 원래 설치 중 선택한 하지 않을 수 있습니다 하는 구성 요소를 설치 하려는 경우 다음 절차를 따르십시오.

#### <a name="to-install-optional-components"></a>선택적 구성 요소를 설치 하려면

1. **제어판**의 **프로그램 및 기능** 페이지에서 하나 이상의 구성 요소를 추가할 제품 버전을 선택한 다음 **변경**을 선택합니다.

2. 설치 마법사에서 **수정**을 선택하고 설치하려는 구성 요소를 선택합니다.

3. **다음**을 선택하고 나머지 지시를 따릅니다.

## <a name="helpContent"></a> 오프라인 도움말 콘텐츠 설치
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 설치하고 나서 추가 도움말 콘텐츠를 다운로드하여 오프라인으로 사용할 수 있습니다.

#### <a name="to-install-or-uninstall-help-content"></a>도움말 콘텐츠를 설치 또는 제거하려면

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 메뉴 모음에서 **도움말**, **도움말 콘텐츠 추가 및 제거**를 선택합니다.

2. **Microsoft 도움말 뷰어** 의 **콘텐츠 관리**탭에서 도움말 콘텐츠의 설치 소스를 선택합니다.

3. 특정 도움말 컬렉션을 찾고자 하는 경우에는 **검색** 텍스트 상자에 이름 또는 키워드를 입력한 다음, **Enter** 키를 누릅니다.

4. 원하는 도움말 컬렉션의 이름 옆에 있는 **추가** 또는 **제거** 링크를 선택합니다.

5. 클릭 합니다 **업데이트** 단추입니다.

   설치 또는 오프 라인 도움말을 배포 하는 방법에 대 한 자세한 내용은 참조는 [도움말 뷰어 관리자 가이드](../ide/help-viewer-administrator-guide.md)합니다.

## <a name="serviceReleases"></a> 서비스 릴리스 및 제품 업데이트 확인
 모든 확장이 호환되는 것은 아니므로 이전 버전에서 업그레이드할 때 Visual Studio에서는 확장을 자동으로 업그레이드하지 않습니다. 확장을 다시 설치 해야 합니다 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 또는 소프트웨어 게시자에서입니다.

#### <a name="to-automatically-check-for-service-releases"></a>서비스 릴리스를 자동으로 확인하려면

1. 메뉴 모음에서 **도구**, **옵션**을 선택합니다.

2. **옵션** 대화 상자에서 **환경**을 확장한 다음 **확장 및 업데이트**를 선택합니다. **자동으로 업데이트 확인** 확인란이 선택되어 있는지 확인한 다음 **확인**을 선택합니다.

## <a name="registering-visual-studio"></a>Visual Studio 등록

1. 메뉴 모음에서 **도움말**, **정보**를 선택합니다.

     **정보** 대화 상자에 PID(제품 등록 번호)가 표시됩니다. 제품을 등록하려면 PID 및 Windows 계정 자격 증명(예: Hotmail 또는 Outlook.com 메일 주소 및 암호)이 필요합니다.

2. 메뉴 모음에서 **도움말**, **제품 등록**을 차례로 선택합니다.

## <a name="repair"></a> Visual Studio 복구

#### <a name="to-repair-visual-studio"></a>Visual Studio를 복구하려면

1. **제어판**의 **프로그램 및 기능** 페이지에서 복구할 제품 버전을 선택한 다음 **변경**을 선택합니다.

2. 설치 마법사에서 **복구**, **다음**을 차례로 선택하고 나머지 지시를 따릅니다.

#### <a name="to-repair-visual-studio-in-silent-or-passive-modes-that-is-to-repair-from-source"></a>자동 또는 수동 모드에서 Visual Studio를 복구 하려면 (즉, 원본에서 복구 하려면)

1. Visual Studio가 설치된 컴퓨터에서 Windows 명령 프롬프트를 엽니다.

2. 다음 매개 변수를 입력합니다.

     *DVDRoot* \\< 설치 파일\> \</quiet&#124;수동/> [/norestart] / 복구

## <a name="troubleshooting"></a> 설치 문제 해결
 다음의 리소스에서 설정 및 설치 관련 문제에 대한 도움말을 참조할 수 있습니다.

- [Visual Studio 설정 및 설치](http://go.microsoft.com/fwlink/?LinkID=151190) 포럼 Visual Studio 커뮤니티에서 다른 사람의 질문과 답변을 검토합니다. 필요한 사항을 찾지 못한 경우 직접 질문을 합니다.

- [Microsoft Visual Studio 지원](http://go.microsoft.com/fwlink/?LinkID=251019) 웹 사이트 KB(기술 자료) 문서를 읽고 Visual Studio 설치 관련 문제에 대한 정보를 얻기 위해 Microsoft 지원에 문의하는 방법을 알아봅니다.

## <a name="relatedTopics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[Visual Studio의 오프라인 설치 만들기](../install/create-an-offline-installation-of-visual-studio.md)|인터넷에 연결 되지 않은 경우 Visual Studio를 설치 하는 방법을 설명 합니다.
|[Visual Studio 버전 병렬 설치](../install/install-visual-studio-versions-side-by-side.md)|같은 컴퓨터에 여러 버전의 Visual Studio를 설치하는 방법에 대한 정보를 제공합니다.|
|[명령줄 매개 변수를 사용하여 Visual Studio 설치](/visualstudio/install/use-command-line-parameters-to-install-visual-studio)|명령 프롬프트에서 Visual Studio를 설치할 때 사용할 수 있는 명령줄 매개 변수를 나열 합니다.|
|[Visual Studio 제거](../install/uninstall-visual-studio.md)|Visual Studio를 제거 하는 방법에 설명 합니다.|
|[Visual Studio 관리자 가이드](../install/visual-studio-administrator-guide.md)|Visual Studio의 배포 옵션에 대한 정보를 제공합니다.|
|[Visual Studio 이미지 라이브러리](../designers/the-visual-studio-image-library.md)|Visual Studio 애플리케이션에서 사용할 수 있는 그래픽을 설치하는 방법에 대한 정보를 제공합니다.|
|[Visual Studio에서 개발 시작](../ide/get-started-developing-with-visual-studio.md)|Visual Studio를 보다 효율적으로 사용할 수 있는 링크와 정보를 포함 합니다.|

## <a name="see-also"></a>참고 항목

- [Visual Studio에 로그인](../ide/signing-in-to-visual-studio.md)