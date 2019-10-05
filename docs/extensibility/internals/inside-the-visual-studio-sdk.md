---
title: Visual Studio SDK 기본 사항 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05736ebc8ce242120b49b59ef6d6caf4c4992573
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349829"
---
# <a name="inside-the-visual-studio-sdk"></a>Visual Studio SDK 기본 사항

이 섹션에서는 Visual Studio 아키텍처, 구성 요소, 서비스, 스키마, 유틸리티 등을 비롯 한 Visual Studio 확장에 대 한 자세한 정보를 제공 합니다.

## <a name="extensibility-architecture"></a>확장성 아키텍처
 다음 그림에서는 Visual Studio 확장성 아키텍처를 보여 줍니다. Vspackage는 서비스와 IDE 간에 공유 되는 응용 프로그램 기능을 제공 합니다. 표준 IDE도 제공 광범위 한 서비스와 같은 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, IDE 창 관리 기능에 대 한 액세스를 제공 하는 합니다.

 ![환경 아키텍처 그래픽](../../extensibility/internals/media/environment.gif "환경") Visual Studio 아키텍처의 보기를 일반화 합니다.

## <a name="vspackages"></a>VSPackages
 VSPackage는 UI 요소, 서비스, 프로젝트, 편집기 및 디자이너를 사용하여 Visual Studio를 구성 및 확장하는 소프트웨어 모듈입니다. Vspackage는 Visual Studio의 중앙 아키텍처 단위입니다. 자세한 내용은 [VSPackages](../../extensibility/internals/vspackages.md)을 참조하세요.

## <a name="visual-studio-shell"></a>Visual Studio Shell
 Visual Studio shell 기본 기능을 제공 하 고 해당 구성 요소 Vspackage 및 MEF 확장 간에 간 통신을 지원 합니다. 자세한 내용은 [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md)합니다.

## <a name="user-experience-guidelines"></a>사용자 환경 지침
 Visual Studio에 대 한 새로운 기능을 디자인 하려는 경우를 살펴보고 디자인 및 유용성 팁에 대 한 이러한 지침을 수행 해야 합니다. [Visual Studio User Experience Guidelines](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)합니다.

## <a name="commands"></a>명령
 명령은 문서 인쇄, 보기 새로 고침 또는 새 파일 만들기 등의 작업을 수행하는 함수입니다.

 Visual Studio를 확장 하는 경우 명령을 만들고 Visual Studio shell을 사용 하 여 등록할 수 있습니다. 이 명령은 표시 되는 방식 IDE에서 예를 들어, 메뉴 또는 도구 모음을 지정할 수 있습니다. 사용자 지정 명령에 표시 되는 일반적으로 **도구** 메뉴와 도구 창을 표시 하는 것에 대 한 명령에 표시 되는 합니다 **다른 Windows** 의 하위 메뉴를 **보기** 메뉴.

 명령을 만들 때에 대 한 이벤트 처리기를 만들 수도 있어야 합니다. 이벤트 처리기 명령을 표시 또는 사용, 해당 텍스트를 수정할 수 있습니다 및 활성화 된 경우 명령이 적절히 응답을 보장 경우를 결정 합니다. 명령을 사용 하 여 IDE에서 대부분의 경우 처리는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 인터페이스입니다. Visual Studio에서 명령은 로컬 선택 영역을 기반으로 하며은 가장 바깥쪽 컨텍스트, 전역 선택 영역을 기반으로 진행 되 고 가장 안쪽의 명령 컨텍스트와 시작으로 처리 됩니다. 주 메뉴에 추가된 명령은 즉시 스크립팅에 사용할 수 있습니다.

 자세한 내용은 [명령, 메뉴 및 도구 모음](../../extensibility/internals/commands-menus-and-toolbars.md)합니다.

## <a name="menus-and-toolbars"></a>메뉴 및 도구 모음
 메뉴 및 도구 모음 명령을 호출할 수 있는 방법을 제공 합니다. 메뉴는 행 또는 열의 일반적으로 도구 창 맨 위에 있는 개별 텍스트 항목으로 표시 되는 명령입니다. 하위 메뉴는 작은 화살표를 포함 하는 명령을 클릭할 때 표시 되는 보조 메뉴. 상황에 맞는 메뉴에는 특정 UI 요소를 클릭할 때 나타납니다. 일부 일반적인 메뉴 이름이 **파일**, **편집**를 **뷰**, 및 **창**합니다. 자세한 내용은 [확장 메뉴 및 명령을](../../extensibility/extending-menus-and-commands.md)합니다.

 도구 모음 단추 및 텍스트 상자, 콤보 상자 및 목록 상자 등의 다른 컨트롤의 행 이나 열 됩니다. 도구 모음 단추에 대 한 폴더 아이콘 같은 아이콘 이미지는 일반적으로 있습니다는 **열려 있는 파일** 명령 또는 프린터를 **인쇄** 명령입니다. 모든 도구 모음 요소가 명령과 사용 하 여 연결 합니다. 도구 모음 단추를 클릭 하면 연결된 된 명령이 실행 됩니다. 드롭다운 목록 컨트롤의 경우 드롭다운 목록에서 각 항목은 다른 명령과 연결 합니다. Splitter 컨트롤과 같은 일부 도구 모음 컨트롤을 갖게 됩니다. 컨트롤의 한 쪽은 도구 모음 단추가 고 아래쪽 화살표를 클릭할 때 몇 가지 명령을 표시 하는 또 다른 측면은입니다.

## <a name="tool-windows"></a>도구 창
 도구 창 정보를 표시 하는 IDE에서 사용 됩니다. **도구 상자**하십시오 **솔루션 탐색기**, **속성** 창 및 **웹 브라우저** 는 도구 창의 예입니다.

 도구 창은 일반적으로 사용자 작용할 수 있는 다양 한 컨트롤을 제공 합니다. 예를 들어 합니다 **속성** 창에는 사용자가 특정 목적으로 사용 되는 개체의 속성을 설정할 수 있습니다. 합니다 **속성** 창 이므로 이런 점에서 특수 하지만 또한 일반 많은 다양 한 상황에서 사용할 수 있습니다. 마찬가지로, 합니다 **출력** 창 많은 하위 시스템 Visual Studio에서 Visual Studio 사용자에 게 출력을 제공 하는 데 사용할 수 있으므로 하지만 일반 텍스트 기반 출력을 제공 하기 때문에 맞게 특별히 설정 됩니다.

 다음 그림의 몇 가지 도구 창을 포함 하는 Visual Studio를 고려 합니다.

 ![스크린 샷](../../extensibility/internals/media/t1gui.png "T1gui")

 도구 창 중 일부는 솔루션 탐색기 도구 창을 표시 하 고 다른 도구 창을 숨깁니다 있지만 탭을 클릭 하 여 사용할 수 있게 하는 단일 창에 함께 도킹 됩니다. 그림과 두 개의 다른 도구 창에는 **오류 목록** 하 고 **출력** 단일 창에 함께 도킹 창입니다.

 여러 편집기 창에 표시 되는 주 문서 창을도 표시 됩니다. 도구 창에는 일반적으로 하나의 인스턴스만 필요는 없지만 (예를 들어 하나만 열 수 있습니다 **솔루션 탐색기**), 편집기 창에 도킹 되는 모든 있지만 별도 문서를 편집 하는 데는 각각의 여러 인스턴스를 가질 수 있습니다 같은 창입니다. 그림에는 두 개의 편집기 창, 하나의 폼 디자이너 창에 있는 문서 창을 보여 줍니다. 문서 창에 있는 모든 창을 탭을 클릭 하 여 사용할 수 있지만 EditorPane.cs 파일이 포함 된 편집기 창이 표시 되 고 활성.

 Visual Studio를 확장할 때 확장을 통해 Visual Studio 사용자가 수 있는 windows 상호 작용 하는 도구를 만들 수 있습니다. 또한 Visual Studio 사용자가 문서를 편집할 수 있는 사용자 고유의 편집기를 만들 수 있습니다. 도구 창 및 편집기에는 Visual Studio에 통합 되어야 하기 때문에 도킹 되거나 탭에 올바르게 표시 하도록 프로그래밍할 필요가 없습니다. Visual Studio에 올바르게 등록 되므로 때 자동으로 도구 창과 문서 창을 Visual Studio에서의 일반적인 기능을 갖습니다. 자세한 내용은 [확장 및 사용자 지정 도구 Windows](../../extensibility/extending-and-customizing-tool-windows.md)합니다.

## <a name="document-windows"></a>문서 창
 문서 창에는 다중 문서 인터페이스 (MDI) 창 프레임이 자식 창이입니다. 문서 창은 텍스트 편집기, 폼 편집기 (라고도 디자이너) 또는 편집 컨트롤을 호스트 하기 일반적으로 사용 되지만 다른 기능 종류를 호스팅할 수도 있습니다. 합니다 **새 파일** 대화 상자에 Visual Studio에서 제공 하는 문서 창의 예입니다.

 대부분의 편집기는 프로그래밍 언어 또는 프레임을 HTML 페이지와 같은 파일 형식에 특정 C++ 파일 또는 헤더 파일입니다. 템플릿을 선택 하 여 합니다 **새 파일** 대화 상자에서 사용자를 동적으로 만듭니다 문서 창 편집기 템플릿과 사용 하 여 연결 된 파일 형식에 대 한 합니다. 사용자가 기존 파일을 열 때 문서 창이 만들어집니다.

 문서 창은 MDI 클라이언트 영역으로 제한 됩니다. 각 문서 창 위쪽에 탭 및 탭 순서 MDI 영역에 열려 있을 수 있는 다른 창에 연결 됩니다. 여러 가로 또는 세로 탭 그룹을 MDI 영역을 분할 하는 옵션을 포함 하는 바로 가기 메뉴를 표시 문서 창의 탭을 마우스 오른쪽 단추로 클릭 합니다. MDI 영역 분할 여러 파일을을 동시에 볼 수 있습니다. 자세한 내용은 [문서 Windows](../../extensibility/internals/document-windows.md)합니다.

## <a name="editors"></a>편집기
 Visual Studio 편집기를 사용 하면 사용자 지정 하 고 사용 하 여는 Framework MEF (Managed Extensibility) 콘텐츠의 고유한 형식에 대해 사용할 수 있습니다. 대부분의 경우에는 셸 (예를 들어 메뉴 명령 또는 바로 가기 키)에서 기능을 포함 하려는 경우에 VSPackage를 사용 하 여 MEF 확장을 결합할 수 있습니다 하지만 편집기를 확장 하기 위해 VSPackage를 만들려면 하지 해야 합니다.

 예를 들어 사용자 지정 편집기를 데이터베이스에 읽기 및 쓰기 하려는 경우 또는 디자이너를 사용 하려는 경우에 만들 수 있습니다. 메모장 이나 Microsoft 워드 패드와 같은 외부 편집기를 사용할 수도 있습니다. 자세한 내용은 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)합니다.

## <a name="language-services"></a>언어 서비스
 새 프로그래밍 키워드 또는 새 프로그래밍 언어를 지원 하기 위해 Visual Studio 편집기를 사용 하도록 하려는 경우에 언어 서비스를 만듭니다. 각 언어 서비스는 완벽 하 게, 부분적으로 또는 전혀 특정 편집기 기능을 구현할 수 있습니다. 구성 방법에 따라 언어 서비스 구문 강조, 중괄호 일치, IntelliSense 지원 및 편집기의 다른 기능을 제공할 수 있습니다.

 언어 서비스의 핵심은 파서 및 스캐너를입니다. 스캐너 (또는 렉서) 소스 파일 토큰 이라고 하는 요소로 나누고 파서 토큰 간의 관계를 설정 합니다. 언어 서비스를 만들면 Visual Studio는 토큰 및 언어의 문법 이해할 수 있도록 파서와 스캐너 구현 해야 합니다. 관리 되거나 관리 되지 않는 언어 서비스를 만들 수 있습니다. 자세한 내용은 [레거시 언어 서비스 확장성](../../extensibility/internals/legacy-language-service-extensibility.md)합니다.

## <a name="projects"></a>프로젝트

Visual Studio에서 프로젝트는 개발자가 구성 하 고 소스 코드 및 기타 리소스를 작성 하는 데 사용할 컨테이너를 사용 합니다. 구성, 빌드, 디버그 및 소스 코드를 배포할 수 있습니다. 프로젝트, 웹 서비스 및 데이터베이스 및 기타 리소스에 대 한 참조입니다. Vspackage는 프로젝트 형식, 프로젝트 하위 형식 및 사용자 지정 도구를 제공 하 여 Visual Studio 프로젝트 시스템을 확장할 수 있습니다.

프로젝트 함께 수집할 수도 있습니다는 *솔루션*, 응용 프로그램을 만들기 위해 함께 작동 하는 하나 이상의 프로젝트의 그룹화 합니다. 솔루션에 관련 된 프로젝트 및 상태 정보는 텍스트를 기반으로 두 솔루션 파일에 저장 됩니다 [솔루션 (.sln) 파일](solution-dot-sln-file.md) 및 이진 [솔루션 사용자 옵션 (.suo) 파일](solution-user-options-dot-suo-file.md)합니다. 이러한 파일은 이전 버전의 Visual Basic의 경우에 사용 된 그룹 (.vbg) 파일 유사 하며 작업 영역 (.dsw) 및 사용자 옵션 (.opt) 파일의 이전 버전에 사용 된 C++입니다.

자세한 내용은 [프로젝트](../../extensibility/internals/projects.md) 하 고 [솔루션](../../extensibility/internals/solutions-overview.md)합니다.

## <a name="project-and-item-templates"></a>프로젝트 및 항목 템플릿
 Visual Studio에는 미리 정의 된 프로젝트 템플릿 및 프로젝트 항목 템플릿을 포함합니다. 사용자 고유의 템플릿을 만들 수도 하 고 또는 커뮤니티에서 템플릿을 가져올 하 고, 다음 Visual Studio에 통합할 수 있습니다. 합니다 [MSDN 코드 갤러리](https://code.msdn.microsoft.com/site/search?query=visual%20studio) 템플릿 및 확장에 대 한 이동할 위치입니다.

 템플릿에 특정 종류의 응용 프로그램, 컨트롤, 라이브러리 또는 클래스를 작성 하는 데 필요한 기본 파일과 프로젝트 구조에 포함 됩니다. 템플릿 중 하 나와 유사한 소프트웨어를 개발 하려는 경우 템플릿을 기반으로 하는 프로젝트를 만들고 해당 프로젝트에서 파일을 수정 합니다.

> [!NOTE]
> 이 템플릿 구조에 대 한 지원 되지 않습니다 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트입니다.

 자세한 내용은 [추가 프로젝트 및 프로젝트 항목 템플릿](../../extensibility/internals/adding-project-and-project-item-templates.md)합니다.

## <a name="properties-and-options"></a>속성 및 옵션
 합니다 **속성** 단일 또는 여러 선택된 항목의 속성 창에 표시 됩니다. [속성 확장](../../extensibility/internals/extending-properties.md) 옵션 페이지, VSPackage 또는 프로그래밍 언어와 같은 특정 구성 요소와 관련 된 옵션 집합을 포함 합니다. [옵션 및 옵션 페이지](../../extensibility/internals/options-and-options-pages.md)합니다. 설정은 일반적으로 UI 관련 기능을 가져오고 내보낼 수 있습니다. [사용자 설정에 대 한 지원을](../../extensibility/internals/support-for-user-settings.md)합니다.

## <a name="visual-studio-services"></a>Visual Studio Services
 서비스 구성 요소를 사용 하는 인터페이스의 특정 집합을 제공 합니다. Visual Studio 확장을 포함 하 여 모든 구성 요소에서 사용할 수 있는 서비스 집합을 제공 합니다. 예를 들어, Visual Studio 서비스를 표시 또는 도움말, 상태 표시줄에 또는 UI 이벤트에 액세스할 수 있도록 동적으로 숨겨진 도구 창을 사용 합니다. Visual Studio 편집기는 또한 편집기 확장에서 가져올 수 있는 서비스를 제공 합니다. 자세한 내용은 [사용 및 제공 서비스](../../extensibility/using-and-providing-services.md)합니다.

## <a name="debugger"></a>디버거
 디버거는 사용자 인터페이스 언어 관련 디버깅 구성 요소입니다. 새 언어 서비스를 만든 경우에 디버거를 연결 하는 특정 디버그 엔진을 만들려고 해야 합니다. 자세한 내용은 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)합니다.

## <a name="source-control"></a>소스 제어
 소스 제어 플러그 인 또는 VSPackage를 구현 하는 방법에 대 한 내용은 [소스 제어](../../extensibility/internals/source-control.md)입니다.

## <a name="wizards"></a>마법사
 해당 형식의 새 프로젝트를 만들 때 사용자가 올바른 결정을 내릴 마법사 도움을 줄 수 있도록, 새 프로젝트 형식을 사용 하 여 마법사를 함께에서 만들 수 있습니다. 자세한 내용은 [마법사](../../extensibility/internals/wizards.md)합니다.

## <a name="custom-tools"></a>사용자 지정 도구
 사용자 지정 도구를 사용 하 여 프로젝트에서 항목을 사용 하 여 도구에 연결 하 고 파일을 저장할 때마다 해당 도구를 실행할 수 있습니다. 자세한 내용은 [사용자 지정 도구](../../extensibility/internals/custom-tools.md)합니다.

## <a name="vssdk-utilities"></a>VSSDK 유틸리티
 VSSDK에 Vspackage의 다양 한 측면을 사용 하기 위해 필요할 수 있는 유틸리티 집합이 포함 됩니다. 자세한 내용은 [VSSDK 유틸리티](../../extensibility/internals/vssdk-utilities.md)합니다.

## <a name="using-windows-installer"></a>Windows Installer를 사용 하 여
 VSIX 설치 관리자를 사용 하지 않고 Windows 설치 관리자를 사용 하도록 해야 할 수 있습니다: 예를 들어, 레지스트리에 쓸 해야 할 수 있습니다. 확장을 사용 하 여 Windows 설치 관리자를 사용 하는 방법에 대 한 내용은 [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)합니다.

## <a name="help-viewer"></a>도움말 뷰어
 고유한 도움말 및 페이지 F1 도움말 뷰어를 통합할 수 있습니다. 자세한 내용은 [Microsoft 도움말 뷰어 SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md)합니다.