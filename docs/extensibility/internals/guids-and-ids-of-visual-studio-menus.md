---
title: Visual Studio 메뉴의 Guid 및 Id | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio menus
- visual studio groups
- id
- existing menus
- guid
- menus
ms.assetid: 84639d86-dd21-4b35-9988-6bb654162488
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26171ae9f4464c3b8b63762d92e9a91d5a4b8420
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329108"
---
# <a name="guids-and-ids-of-visual-studio-menus"></a>Guid 및 Id의 Visual Studio 메뉴
이 문서에서는 메뉴 및 Visual Studio 메뉴 모음에서 그룹의 GUID 및 ID 값을 열거합니다. 이러한 값에 정의 된 *.vsct* Visual Studio SDK의 일부로 설치 되는 파일입니다. 자세한 내용은 [IDE 정의 명령, 메뉴 및 그룹](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)합니다.

 에 정의 된 통합된 개발 환경 (IDE) 개체를 사용 하는 방법에 대 한 자세한 내용은 *.vsct* 파일을 참조 하십시오 [메뉴와 명령을 확장](../../extensibility/extending-menus-and-commands.md)합니다.

 메뉴 및 Visual Studio 메뉴 모음에서 그룹을 사용 하 여 GUID `guidSHLMainMenu`합니다. 메뉴 모음 자체 ID가 `IDM_VS_TOOL_MAINMENU`입니다.

## <a name="groups-on-the-visual-studio-menu-bar"></a>Visual Studio 메뉴 모음에서 그룹
 메뉴 모음에 메뉴를 추가 하려면 이러한 그룹 중 하나를 부모로 설정 합니다.

|그룹화|ID|
|-----------|--------|
|파일/편집/보기|IDG_VS_MM_FILEEDITVIEW|
|리팩터링|IDG_VS_MM_REFACTORING:|
|프로젝트|IDG_VS_MM_PROJECT|
|빌드|IDG_VS_MM_BUILDDEBUGRUN|
|형식/도구|IDG_VS_MM_TOOLSADDINS|
|창/도움말/Community|IDG_VS_MM_WINDOWHELP|
|추가 기능|IDG_VS_MM_MACROS|
|FullScreenBar|IDG_VS_MM_FULLSCREENBAR|

## <a name="menus-on-the-visual-studio-menu-bar"></a>Visual Studio 메뉴 모음에서 메뉴
 기존 Visual Studio 메뉴에는 그룹을 추가 하려면 다음 메뉴 중 하나를 부모로 설정 합니다. 이 목록에 하위 메뉴가 포함 되지 않습니다.

|메뉴|ID|
|----------|--------|
|파일|IDM_VS_MENU_FILE|
|편집|IDM_VS_MENU_EDIT|
|보기|IDM_VS_MENU_VIEW|
|리팩터링|IDM_VS_MENU_REFACTORING|
|프로젝트|IDM_VS_MENU_PROJECT|
|빌드|IDM_VS_MENU_BUILD|
|형식|IDM_VS_MENU_FORMAT|
|도구|IDM_VS_MENU_TOOLS|
|확장|IDM_VS_MENU_EXTENSIONS|
|창|IDM_VS_MENU_WINDOW|
|추가 기능|IDM_VS_MENU_ADDINS|
|커뮤니티|IDM_VS_MENU_COMMUNITY|
|Help|IDM_VS_MENU_HELP|

## <a name="groups-on-visual-studio-menus"></a>Visual Studio 메뉴에는 그룹
 다음 목록에서는 Visual Studio 메뉴 모음에서 메뉴에서 직접 물려받은 그룹을 나타냅니다. Visual Studio 메뉴에 명령을 추가 하는 가장 빠른 방법은 부모로 이러한 그룹 중 하나를 설정 하는 것입니다. 이 섹션에는 하위 메뉴에서 물려받은 그룹 표시 되지 않습니다.

### <a name="file-menu-groups"></a>파일 메뉴 그룹

|그룹화|ID|
|-----------|--------|
|새로 만들기/열기|IDG_VS_FILE_FILE|
|Add|IDG_VS_FILE_ADD|
|솔루션|IDG_VS_FILE_SOLUTION|
|기타|IDG_VS_FILE_MISC|
|Save|IDG_VS_FILE_SAVE|
|이름 바꾸기|IDG_VS_FILE_RENAME|
|브라우저|IDG_VS_FILE_BROWSER|
|용|IDG_VS_FILE_PRINT|
|가장 최근에 사용 됨|IDG_VS_FILE_MRU|
|이동|IDG_VS_FILE_MOVE|
|종료|IDG_VS_FILE_EXIT|

### <a name="edit-menu-groups"></a>메뉴 그룹 편집

|그룹화|ID|
|-----------|--------|
|실행 취소/다시 실행|IDG_VS_EDIT_UNDOREDO|
|잘라내기/복사/붙여넣기|IDG_VS_EDIT_CUTCOPY|
|선택|IDG_VS_EDIT_SELECT|
|GoTo|IDG_VS_EDIT_GOTO|
|Find|IDG_VS_EDIT_FIND|
|개체|IDG_VS_EDIT_OBJECTS|
|OLE 동사|IDG_VS_EDIT_OLEVERBS|
|도 명령|IDG_VS_EDIT_COMMANDWELL|

### <a name="refactor-menu-groups"></a>리팩터링 메뉴 그룹

|그룹화|ID|
|-----------|--------|
|공용|IDG_REFACTORING_COMMON|
|고급|IDG_REFACTORING_ADVANCED|

### <a name="view-menu-groups"></a>메뉴 그룹 보기

|그룹화|ID|
|-----------|--------|
|폼 코드|IDG_VS_VIEW_FORMCODE|
|브라우저|IDG_VS_VIEW_BROWSER|
|뷰를 정의 합니다.|IDG_VS_VIEW_DEFINEVIEWS|
|Windows|IDG_VS_VIEW_WINDOWS|
|Windows를 설계 합니다.|IDG_VS_VIEW_ARCH_WINDOWS|
|조직의 Windows|IDG_VS_VIEW_ORG_WINDOWS|
|코드 브라우저|IDG_VS_VIEW_CODEBROWSENAV_WINDOWS|
|Dev Windows|IDG_VS_VIEW_DEV_WINDOWS|
|도구 모음|IDG_VS_VIEW_TOOLBARS|
|기호|IDG_VS_VIEW_SYMBOLNAVIGATE|
|이동|IDG_VS_VIEW_NAVIGATE|
|작은 이동|IDG_VS_VIEW_SMALLNAVIGATE|
|개체 브라우저|IDG_VS_VIEW_OBJBRWSR|
|도 명령|IDG_VS_VIEW_COMMANDWELL|
|속성 페이지|IDG_VS_VIEW_PROPPAGES|
|새로 고침|IDG_VS_VIEW_REFRESH|

### <a name="project-menu-groups"></a>프로젝트 메뉴 그룹

|그룹화|ID|
|-----------|--------|
|기타 추가|IDG_VS_PROJ_MISCADD|
|Add|IDG_VS_PROJ_ADD|
|폴더|IDG_VS_PROJ_FOLDER|
|언로드/다시 로드|IDG_VS_PROJ_UNLOADRELOAD|
|참조|IDG_VS_PROJ_REFERENCE|
|옵션|IDG_VS_PROJ_OPTIONS|
|설정|IDG_VS_PROJ_SETTINGS|

### <a name="build-menu-groups"></a>빌드 메뉴 그룹

|그룹화|ID|
|-----------|--------|
|솔루션|IDG_VS_BUILD_SOLUTION|
|선택|IDG_VS_BUILD_SELECTION|
|프로필 기반 최적화|IDG_VS_PGO_SELECTION|
|기타|IDG_VS_BUILD_MISC|
|취소|IDG_VS_BUILD_CANCEL|

### <a name="tools-menu-groups"></a>도구 메뉴 그룹

|그룹화|ID|
|-----------|--------|
|명령줄|IDG_VS_TOOLS_CMDLINE|
|코드 조각|IDG_VS_TOOLS_SNIPPETS|
|개체 하위 집합|IDG_VS_TOOLS_OBJSUBSET|
|옵션|IDG_VS_TOOLS_OPTIONS|
|다른 2|IDG_VS_TOOLS_OTHER2|
|외부 도구|IDG_VS_TOOLS_EXT_TOOLS|
|외부 사용자 지정|IDG_VS_TOOLS_EXT_CUST|

### <a name="window-menu-groups"></a>창 메뉴 그룹

|그룹화|ID|
|-----------|--------|
|새로 만들기|IDG_VS_WINDOW_NEW|
|도킹/닫기|IDG_VS_DOCKCLOSE|
|도킹/숨기기|IDG_VS_DOCKHIDE|
|정렬|IDG_VS_WINDOW_ARRANGE|
|탐색|IDG_VS_WINDOW_NAVIGATION|
|목록|IDG_VS_WINDOW_LIST|

### <a name="help-menu-groups"></a>도움말 메뉴 그룹

|그룹화|ID|
|-----------|--------|
|샘플|IDG_VS_HELP_SAMPLES|
|Support(지원)|IDG_VS_HELP_SUPPORT|
|정보|IDG_VS_HELP_ABOUT|

## <a name="submenus-of-visual-studio-menus"></a>Visual Studio 메뉴의 하위 메뉴
 다음 계층에서는 Visual Studio 메뉴 모음에서 메뉴와 연결 된 하위 메뉴를 보여 줍니다. 그룹만 부모로 메뉴를 가질 수 있으므로 모든 하위 메뉴 해야 내림차순 그룹에서 메뉴의 대신 메뉴에서 직접. 메뉴, 그룹 및 하위 메뉴 간의 관계에 대 한 자세한 내용은 참조 하세요. [하위 메뉴에 추가](../../extensibility/adding-a-submenu-to-a-menu.md)합니다.

> [!NOTE]
> Visual Studio 메뉴 모음에서 메뉴 이름은 별도로이 계층에서 때문에 표시 되지 다음과 같이 IDE에서 그룹에 대 한 명명 규칙에서 유추할 수 있습니다. *IDG_VS_\<메뉴 이름\>_\<그룹 이름\>* 합니다.

|부모 그룹|하위 메뉴|자식 그룹|
|------------------|-------------|------------------|
|IDG_VS_FILE_FILE|IDM_VS_CSCD_NEW|IDG_VS_FILE_NEW_CASCADE|
||IDM_VS_CSCD_OPEN|IDG_VS_FILE_OPENP_CASCADE|
|||IDG_VS_FILE_OPENF_CASCADE|
|IDG_VS_FILE_ADD|IDM_VS_CSCD_ADD|IDG_VS_FILE_ADD_PROJECT_NEW|
|||IDG_VS_FILE_ADD_PROJECT_EXI|
|IDG_VS_FILE_MRU|IDM_VS_CSCD_FILEMRU|IDG_VS_FILE_FMRU_CASCADE|
||IDM_VS_CSCD_PROJMRU|IDG_VS_FILE_PMRU_CASCADE|
|IDG_VS_FILE_MOVE|IDM_VS_CSCD_MOVETOPRJ|IDG_VS_FILE_MOVE_CASCADE|
|||IDG_VS_FILE_MOVE_PICKER|
|IDG_VS_VIEW_DEV_WINDOWS|IDM_VS_CSCD_FINDRESULTS|IDG_VS_WNDO_FINDRESULTS|
||IDM_VS_CSCD_WINDOWS|IDG_VS_VIEW_CALLBROWSER|
|||IDG_VS_WNDO_OTRWNDWS1...6|
|||IDG_VS_WNDO_WINDOWS2|
|IDG_VS_VIEW_TOOLBARS|IDM_VS_CSCD_COMMANDBARS||
|IDG_VS_EDIT_GOTO|IDM_VS_EDITOR_FIND_MENU||
|IDG_VS_EDIT_OBJECTS|IDM_VS_CSCD_MNUDES|IDG_VS_MNUDES_INSERT|
|||IDG_VS_MNUDES_EDITNAMES|
||IDM_VS_CSCD_OLEVERBS|IDG_VS_EDIT_OLEVERBS|
|IDG_VS_BUILD_SELECTION|IDM_VS_CSCD_BUILD|IDG_VS_BUILD_CASCADE|
|||IDG_VS_BUILD_PROJPICKER|
||IDM_VS_CSCD_REBUILD|IDG_VS_REBUILD_CASCADE|
|||IDG_VS_REBUILD_PROJPICKER|
||IDM_VS_CSCD_PROJONLY|IDG_VS_PROJONLY_CASCADE|
||IDM_VS_CSCD_CLEAN|IDG_VS_CLEAN_CASCADE|
|||IDG_VS_CLEAN_PROJPICKER|
||IDM_VS_CSCD_DEPLOY|IDG_VS_DEPLOY_CASCADE|
|||IDG_VS_DEPLOY_PROJPICKER|
|IDG_VS_PGO_SELECTION|IDM_VS_CSCD_PGO_BUILD|IDG_VS_PGO_BUILD_CASCADE_BUILD|
|||IDG_VS_PGO_BUILD_CASCADE_RUN|

## <a name="see-also"></a>참고자료
- [Guid 및 Id의 Visual Studio 도구 모음](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)
- [Guid 및 Id의 Visual Studio 명령](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)
- [Visual Studio 명령 테이블 (.vsct) 파일](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
