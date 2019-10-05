---
title: 격리 셸 사용자 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode
ms.assetid: e0b7c3ae-210f-4f48-ac49-6a59e6034f5f
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 724d4d0c4b392a362e702f33ea996df3a6fc0ad6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555971"
---
# <a name="customizing-the-isolated-shell"></a>격리 셸 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 사용자 인터페이스의 다양 한 측면을 변경 하 고 명령 및 특수화 된 응용 프로그램에 포함 된 기능을 제한 하 여 Visual Studio 격리 셸 응용 프로그램을 사용자 지정할 수 있습니다.  
  
## <a name="using-the-applicationpkgdef-file"></a>Application.pkgdef 파일 사용  
 격리 셸 템플릿 솔루션에 포함 된 *SolutionName*합니다. 다음과 같은 기능을 수정할 수 있는 Application.pkgdef 파일:  
  
##### <a name="the-application-title"></a>응용 프로그램 제목  
 이름에 "AppName" 행의 값을 변경 하 여 응용 프로그램의 제목 표시줄에 표시 되는 응용 프로그램 제목 사용자 지정할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다. 자세한 내용은 참조 하세요. [연습: 격리 셸 응용 프로그램을 만드는 기본](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)입니다.  
  
 응용 프로그램 제목을 현재 로드 된 프로젝트를 표시 하지 않으려면 "ShowHierarchyRootInTitle" 행의 값을 변경 합니다 *SolutionName*합니다. dword:00000001 파일 dword:00000000은 Application.pkgdef입니다.  
  
##### <a name="the-application-icon"></a>응용 프로그램 아이콘  
 응용 프로그램 제목 표시줄에 응용 프로그램 이름으로 표시 되는 아이콘으로 표시 하는 응용 프로그램 아이콘을 사용자 지정할 수 있습니다. 다른 아이콘 아이콘 디렉터리로 복사 합니다. **솔루션 탐색기**, 리소스 파일 폴더 아이콘을 추가 합니다. VSShellStub.rc 파일을 열고 IDI_STUBPROGRAM 변수의 새 아이콘의 이름으로 바꿉니다. 자세한 내용은 참조 하세요. [연습: 격리 셸 응용 프로그램을 만드는 기본](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)입니다.  
  
##### <a name="the-command-line-logo"></a>명령줄 로고  
 응용 프로그램에서 "CommandLineLogo" 행의 값을 변경 하 여 명령줄에서 시작 될 때 나타나는 텍스트는 명령줄 로고를 사용자 지정할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다. 자세한 내용은 참조 하세요. [연습: 기본 격리 셸 애플리케이션 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="the-name-of-the-user-files-subfolder"></a>사용자 파일 하위 폴더의 이름  
 "UserFilesSubFolderName" 행의 값을 변경 하 여 사용자 파일에 대 한 유지 관리 응용 프로그램 폴더의 이름을 변경할 수 있습니다 *SolutionName*합니다. Application.pkgdef 파일입니다.  
  
##### <a name="the-title-of-the-solution-tree-node-in-the-new-project-dialog"></a>새 프로젝트 대화 상자에서 솔루션 트리 노드의 제목  
 "NewProjDlgSlnTreeNodeTitle" 행의 값을 변경 하 여 제목의 새 프로젝트 대화 상자에서 솔루션 노드를 사용자 지정할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다.  
  
##### <a name="the-installed-templates-header-in-the-new-project-dialog"></a>새 프로젝트 대화 상자의 설치 된 템플릿 헤더  
 "NewProjDlgInstalledTemplatesHdr" 행의 값을 변경 하 여 새 프로젝트 대화 상자의 설치 된 템플릿 헤더를 변경할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다.  
  
##### <a name="whether-or-not-to-hide-miscellaneous-files-by-default"></a>기본적으로 기타 파일을 숨길 것인지 여부  
 기타 파일을 기본적으로 "HideMiscellaneousFilesByDefault" 행의 값을 변경 하 여 숨길 것인지 여부를 지정할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다. 기타 파일을 숨기려면 값을 설정 `dword:00000001`, 파일을 표시 하려면 값을 설정 하 고 `dword:00000000`입니다.  
  
##### <a name="whether-or-not-to-disable-the-output-window"></a>출력 창 사용 안 함 여부  
 응용 프로그램의 출력 창에 있는 "DisableOutputWindow" 행의 값을 변경 하 여 사용 하지 않도록 것인지 여부를 지정할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다. [출력] 창의 사용 하지 않으려면 값을 설정 `dword:00000001`, 출력 창에 표시 하려면 값을 설정 하 고 `dword:00000000`입니다.  
  
##### <a name="whether-or-not-to-allow-dropped-files-on-the-main-window"></a>주 창에서 끌어 놓은 파일을 허용 하는지 여부  
 "AllowsDroppedFilesOnMainWindow" 행의 값을 변경 하 여 응용 프로그램의 주 창에 끌어 놓은 파일을 허용 하는지 여부를 지정할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다. 끌어 놓은 파일을 허용 하려면 값을 설정 `dword:00000001`에서 끌어 놓은 파일을 허용 하지 않을 값을 설정 하 고 `dword:00000000`입니다.  
  
##### <a name="the-default-search-page"></a>기본 검색 페이지  
 가 열리면 웹 브라우저 창에서 "DefaultSearchPage" 행의 값을 변경 하 여 표시 되는 페이지는 웹 브라우저 페이지를 사용자 지정할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다.  
  
##### <a name="the-default-home-page"></a>기본 홈 페이지  
 홈페이지에서 "DefaultHomePage" 행의 값을 변경 하 여 사용자 지정할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다. 자세한 내용은 참조 하세요. [연습: 기본 격리 셸 애플리케이션 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)  
  
##### <a name="whether-or-not-to-hide-the-solution-concept"></a>솔루션 개념을 숨길 것인지 여부  
 "HideSolutionConcept" 행의 값을 변경 하 여 응용 프로그램에서 솔루션을 숨길 것인지 여부를 지정할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다. 값을 설정 하는 솔루션을 숨기려면 `dword:00000001`, 솔루션을 보여 주기 위해 값을 설정 하 고 `dword:00000000`입니다.  
  
##### <a name="the-default-debug-engine"></a>기본 디버그 엔진  
 "DefaultDebugEngine" 행의 값을 변경 하 여 응용 프로그램에서 사용 하는 디버그 엔진을 변경할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일 디버그 엔진의 GUID입니다.  
  
##### <a name="the-file-extension-of-the-user-options-file"></a>사용자 옵션 파일의 파일 확장명  
 "UserOptsFileExt" 행의 값을 변경 하 여 사용자 파일에 대 한 유지 관리 응용 프로그램 폴더의 이름을 변경할 수 있습니다 *SolutionName*합니다. Application.pkgdef 파일입니다.  
  
##### <a name="the-solution-file-extension"></a>솔루션 파일 확장명  
 "SolutionFileExt" 행의 값을 변경 하 여 솔루션 파일에 대해 사용 되는 확장을 변경할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다.  
  
##### <a name="the-default-user-files-folder-root"></a>기본 사용자 파일의 폴더 루트  
 "UserFilesSubFolderName" 행의 값을 변경 하 여 응용 프로그램에 대 한 사용자 파일의 루트 폴더의 이름을 변경할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다.  
  
##### <a name="the-solution-file-creator-identifier"></a>솔루션 파일 작성자 식별자  
 "SolutionFileCreatorIdentifier" 행의 값을 변경 하 여 솔루션 파일에 대해 사용 하는 식별자를 변경할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다.  
  
##### <a name="the-default-projects-location"></a>기본 프로젝트 위치  
 "DefaultProjectsLocation" 행의 값을 변경 하 여 기본 프로젝트 위치 이름을 바꾸면 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다.  
  
##### <a name="the-application-localization-package"></a>응용 프로그램 지역화 패키지  
 "AppLocalizationPackage" 행의 값을 변경 하 여 응용 프로그램에 대해 사용 하는 지역화 패키지를 변경할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다.  
  
##### <a name="whether-or-not-to-show-the-hierarchy-root-in-the-title"></a>계층 루트 제목에 표시 여부  
 계층 루트를 "ShowHierarchyRootInTitle" 행의 값을 변경 하 여 응용 프로그램의 제목 표시줄에서 표시 여부를 지정할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다. 계층 루트를 표시 하려면 값을 설정 `dword:00000001`, 계층 구조의 루트를 숨기려면 값을 설정 하 고 `dword:00000000`입니다.  
  
##### <a name="specifying-a-start-page"></a>시작 페이지를 지정합니다.  
 사용자 지정 응용 프로그램에 대 한 시작 페이지를 지정 하는 *SolutionName*합니다. Application.pkgdef 파일인 "DisableStartPage" 값을 설정 합니다 `dword:00000000`, 고 `[$RootKey$\StartPage\Default]` .xaml 파일의 위치로 URI를 설정 합니다.  
  
```  
DisableStartPage=dword:00000000  
[$RootKey$\StartPage\Default]  
"Uri"="$RootFolder$\<name of XAML file>"  
```  
  
 Applicationcommands.vsct 파일에는 *SolutionName*UI 프로젝트를 "No_ShellPkg_startPageCommand" 항목을 주석:  
  
```  
<!--<Define name="No_ShellPkg_StartPageCommand"/>-->  
```  
  
 에 필요한 모든 그래픽 파일과.xaml 파일을 추가 해야 합니다 *SolutionName* 프로젝트입니다. 이러한 파일에 실제로 복사 해야 합니다 *SolutionName* 프로젝트 디렉터리를 다른 디렉터리에서 추가 되지 않습니다.  
  
 모든 파일을 설정 합니다 **항목 형식** 속성을 **격리 된 셸 파일** 순서로 파일을 복사할 수는 *$RootFolder$* 디렉터리. (설정 하는 **항목 형식** 속성에 파일을 마우스 오른쪽 단추로 클릭 하 고 선택 **속성**합니다. 이 속성은 아래 **구성 속성**하십시오 **일반**.)  
  
 시작 페이지 사용자 지정에 대 한 자세한 내용은 참조 하세요. [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)합니다.  
  
## <a name="using-other-elements-of-the-isolated-shell"></a>격리 셸의 다른 요소를 사용 하 여  
 다른 파일 및 응용 프로그램을 추가로 사용자 지정 하는 격리 셸 솔루션 템플릿에 포함 된 프로젝트를 사용할 수 있습니다.  
  
##### <a name="enabledisable-visual-studio-packages"></a>Visual Studio 패키지 사용/사용 안 함  
 합니다 *SolutionName*.pkgundef 파일을 사용 하면 특정 패키지를 제외 하 여 특정 종류의 Visual Studio 기능을 해제할 수 있습니다. 예를 들어 다음 줄:  
  
```  
[$RootKey$\Projects\{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}\AddItemTemplates\TemplateDirs\{39c9c826-8ef8-4079-8c95-428f5b1c323f}]  
```  
  
 기타 파일 프로젝트에 표시 되는 프로젝트 템플릿 집합에서 제거 합니다 **새 프로젝트** 대화 합니다. 자세한 내용은 참조 하세요. [연습: 격리 셸 응용 프로그램을 만드는 기본](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)입니다.  
  
##### <a name="enabledisable-menu-commands"></a>설정/해제 메뉴 명령  
 합니다 *SolutionName*UI.vsct 파일에 isolated shell을 사용할 수 있는 모든 메뉴 명령의 주석 목록이 포함 됩니다. 지정된 된 명령을 사용 하지 않으려면 해당 행을 주석 처리 제거 합니다. 예를 들어 창/분할 주석을 사용 하지 않도록 설정, 주석 처리를 제거 합니다 `<Define name="No_SplitCommand"/>` 행입니다. 자세한 내용은 참조 하세요. [연습: 격리 셸 응용 프로그램을 만드는 기본](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)입니다.  
  
##### <a name="the-bitmap-used-on-the-splash-screen"></a>시작 화면에 사용 되는 비트맵  
 시작 화면에는 "SplashScreenBitmap" 행의 값을 변경 하 여 응용 프로그램이 시작 될 때 표시 되는 창에서 사용 되는 비트맵을 사용자 지정할 수 있습니다 합니다 *SolutionName*합니다. Application.pkgdef 파일입니다. 자세한 내용은 참조 하세요. [연습: 격리 셸 응용 프로그램을 만드는 기본](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)입니다.  
  
##### <a name="the-helpabout-window"></a>도움말/창 정보  
 격리 셸 템플릿에서 도움말을 사용자 지정 하 여 별도 프로젝트/응용 프로그램에 대 한 상자에 대 한 합니다. 자세한 내용은 참조 하세요. [연습: 격리 셸 응용 프로그램을 만드는 기본](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)입니다.
