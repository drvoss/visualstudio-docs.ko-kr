---
title: Visual Studio 도구 모음의 Guid 및 Id | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio groups
- toolbars
- visual studio toolbar
- id
- toolgar group
- tool window toolbar
- guid
ms.assetid: c9cacd57-9225-450f-a9ac-cbf3168ea844
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62384942bb0577860161f8ae11d2eb6e787257bf
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328892"
---
# <a name="guids-and-ids-of-visual-studio-toolbars"></a>Guid 및 Id의 Visual Studio 도구 모음
이 항목에서는 Visual Studio 통합된 개발 환경 (IDE)에 포함 된 도구 모음의 GUID 및 ID 값을 열거 하 고 포함 된 그룹의 키를 누릅니다. 이러한 값에 정의 된 *.vsct* Visual Studio SDK의 일부로 설치 되는 파일입니다. 자세한 내용은 [IDE 정의 명령, 메뉴 및 그룹](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)합니다.

> [!NOTE]
> 다양 한 Visual Studio에 사용할 수 있는 도구는 Visual Studio 및 GUID가 정의 되어 있지 않은 및 ID 값 public이 아니어야 합니다. 이 항목에서는 Visual Studio SDK에 정의 된 도구 모음만 나열 *.vsct* 파일입니다.

 에 정의 된 IDE 개체를 사용 하는 방법에 대 한 자세한 내용은 *.vsct* 파일을 참조 하십시오 [메뉴와 명령을 확장](../../extensibility/extending-menus-and-commands.md)합니다.

 GUID를 사용 하는 Visual Studio IDE에서 제공 하는 기본 도구 모음 `guidSHLMainMenu`를 사용 하 여 지정 하는 경우를 제외 하 고 `GUID:ID` 구문입니다.

## <a name="ide-toolbars"></a>IDE 도구 모음
 다음 도구는 Visual Studio IDE에서 제공 됩니다. 도구 모음에서 선택 하 여 표시할 수는 **도구 모음** 의 하위 메뉴의 **도구** 메뉴. 이 섹션의 도구 창에서 도구 모음 포함 되지 않습니다.

 도구 모음에서 직접 그룹만 내림차순 수 있습니다. 그룹을 추가 하려면 도구 모음의 ID GUID를 부모를 설정 합니다. 도구 모음에 단추를 추가할 그룹에 부모 도구 모음에서 설정 합니다.

|ToolBar|ID|
|-------------|--------|
|표준|IDM_VS_TOOL_STANDARD|
|빌드|IDM_VS_TOOL_BUILD|
|텍스트 편집기|IDM_VS_TOOL_TEXTEDITOR|
|디버그|guidVSDebugGroup:IDM_DEBUG_TOOLBAR|
|디버그 위치|guidVSDebugGroup:IDM_DEBUG_CONTEXT_TOOLBAR|

### <a name="special-toolbars"></a>특수 도구 모음
 이러한 도구 모음 Visual Studio IDE에 의해 정의 되지만 특수 기능을 제공 하며 명령 그룹을 호스트 하지 않습니다.

|ToolBar|ID|
|-------------|--------|
|Add 명령|IDM_VS_TOOL_ADDCOMMAND|
|Undefined|IDM_VS_TOOL_UNDEFINED|
|XML 스키마|IDM_VS_TOOL_SCHEMA|
|XML 데이터|IDM_VS_TOOL_DATA|

## <a name="groups-on-the-ide-toolbars"></a>IDE 도구 모음에는 그룹
 표준 도구 모음에 단추를 추가 하려면 다음 그룹 중 하나를 부모로 설정 합니다. 그룹은 부모 도구 모음으로 정렬 됩니다.

### <a name="standard-toolbar-groups"></a>표준 도구 모음 그룹

|이름|ID|
|----------|--------|
|저장/열기|IDG_VS_TOOLSB_SAVEOPEN|
|잘라내기/복사|IDG_VS_TOOLSB_CUTCOPY|
|실행 취소/다시 실행|IDG_VS_TOOLSB_UNDOREDO|
|실행/빌드|IDG_VS_TOOLSB_RUNBUILD|
|검색|IDG_VS_TOOLSB_SEARCH|
|Windows|IDG_VS_TOOLSB_WINDOWS|
|새 창|IDG_VS_TOOLSB_NEWWINDOWS|
|로드/저장|IDG_VS_WINDOWUI_LOADSAVE|
|계기|IDG_VS_TOOLSB_GAUGE|

### <a name="build-toolbar-groups"></a>빌드 도구 모음 그룹

|이름|ID|
|----------|--------|
|빌드 표시줄|IDG_VS_BUILDBAR|
|취소|IDG_VS_BUILD_CANCEL|

### <a name="text-editor-toolbar-groups"></a>텍스트 편집기 도구 모음 그룹

|이름|ID|
|----------|--------|
|완료|IDM_VS_TOOL_TEXTEDITOR|
|Indent|IDG_VS_EDITTOOLBAR_INDENT|
|주석|IDG_VS_EDITTOOLBAR_COMMENT|
|책갈피|IDG_VS_EDITTOOLBAR_TEMPBOOKMARKS|

### <a name="debug-toolbar-groups"></a>디버그 도구 모음 그룹

|이름|ID|
|----------|--------|
|실행|IDM_DEBUG_TOOLBAR|
|단계별 실행|IDG_DEBUG_TOOLBAR_STEPPING|
|조사식|IDG_DEBUG_TOOLBAR_WATCH|
|Windows|IDG_DEBUG_TOOLBAR_WINDOWS|

### <a name="debug-location-toolbar-groups"></a>디버그 위치 도구 모음 그룹

|이름|ID|
|----------|--------|
|디버그 위치|IDG_DEBUG_CONTEXT_TOOLBAR|

## <a name="tool-window-toolbars"></a>도구 창 도구 모음
 도구 모음 도구 창 또는 IDE에서 직접와 같이 나타날 수 **솔루션 탐색기**합니다. 도구 창에 정의 되어 있지 않은 때문 *.vsct* 파일, 도구 창 도구 모음 부모가 정의 되지 않습니다. 대신 코드에 배치 됩니다. 다음 표에서 IDE에서 도구 창에 표시 되는 도구 모음 및 포함 된 명령 그룹을 보여 줍니다.

> [!NOTE]
> 도구 모음 및 그룹의 GUID를 사용 하 여 `guidSHLMainMenu`, guid: id 구문을 사용 하 여 지정 하는 경우를 제외 합니다. 도구 모음에 대 한 GUID를 지정 하는 경우 해당 도구 모음에서 물려받은 그룹에도 적용 됩니다.

|도구 창|ToolBar|그룹|
|-----------------|-------------|------------|
|솔루션 탐색기|IDM_VS_TOOL_PROJWIN|IDG_VS_PROJ_TOOLBAR1..5|
|서버 탐색기|guid_SE_MenuGroup:IDM_SE_TOOLBAR_SERVEREXPLORER|IDG_SE_TOOLBAR_REFRESH|
|속성|IDM_VS_TOOL_PROPERTIES|IDG_VS_PROPERTIES_SORT<br /><br /> IDG_VS_PROPERTIES_PAGES|
|클래스 뷰|IDM_VS_TOOL_CLASSVIEW|IDG_VS_CLASSVIEW_FOLDERS<br /><br /> IDG_VS_CLASSVIEW_SEARCH<br /><br /> IDG_VS_CLASSVIEW_SETTINGS|
|클래스 뷰|IDM_VS_TOOL_CLASSVIEW_GO|IDG_VS_CLASSVIEW_SEARCH2|
|개체 브라우저|IDM_VS_TOOL_OBJBROWSER|IDG_VS_OBJBROWSER_SUBSETS<br /><br /> IDG_VS_OBJBROWSER_SEARCH<br /><br /> IDG_VS_OBJBROWSER_ADDREFERENCE<br /><br /> IDG_VS_OBJBROWSER_BROWSERSETTINGS|
|개체 브라우저|IDM_VS_TOOL_OBJECT_BROWSER_GO|IDG_VS_OBJBROWSER_SEARCH2|
|출력|IDM_VS_TOOL_OUTPUTWINDOW|IDG_VS_OUTPUTWINDOW_SELECT<br /><br /> IDG_VS_OUTPUTWINDOW_GOTO<br /><br /> IDG_VS_OUTPUTWINDOW_NEXTPREV<br /><br /> IDG_VS_OUTPUTWINDOW_CLEAR<br /><br /> IDG_VS_OUTPUTWINDOW_WORDWRAP|
|찾기 및 바꾸기|IDM_VS_TOOL_UNIFIEDFIND|IDG_VS_FINDTAB<br /><br /> IDG_VS_REPLACETAB|
|찾기 결과 1|IDM_VS_TOOL_FINDRESULTS1|IDG_VS_FINDRESULTS1_GOTO<br /><br /> IDG_VS_FINDRESULTS1_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS1_CLEAR<br /><br /> IDG_VS_FINDRESULTS1_STOPFIND|
|찾기 결과 2|IDM_VS_TOOL_FINDRESULTS2|IDG_VS_FINDRESULTS2_GOTO<br /><br /> IDG_VS_FINDRESULTS2_NEXTPREV<br /><br /> IDG_VS_FINDRESULTS2_CLEAR<br /><br /> IDG_VS_FINDRESULTS2_STOPFIND|
|코드 조각|IDM_VS_TOOL_SNIPPETMENUS|IDG_VS_SNIPPET_REPL<br /><br /> IDG_VS_SNIPPET_REF<br /><br /> IDG_VS_SNIPPET_PROP|
|책갈피|IDM_VS_TOOL_BOOKMARKWIND|IDG_VS_BWNEWFOLDER<br /><br /> IDG_VS_BWNEXTBM<br /><br /> IDG_VS_BWNEXTBMF<br /><br /> IDG_VS_BWENABLE<br /><br /> IDG_VS_BWDELETE|
|작업 목록|IDM_VS_TOOL_TASKLIST|IDG_VS_TASKLIST_PROVIDERLIST|
|사용자 작업|IDM_VS_TOOL_USERTASKS|IDG_VS_TASKLIST_PROVIDERLIST<br /><br /> IDG_VS_USERTASKS_EDIT|
|오류 목록|IDM_VS_TOOL_ERRORLIST|IDG_VS_ERRORLIST_ERRORGROUP<br /><br /> IDG_VS_ERRORLIST_WARNINGGROUP<br /><br /> IDG_VS_ERRORLIST_MESSAGEGROUP|
|호출 브라우저|IDM_VS_TOOL_CALLBROWSER1..16|IDG_VS_TOOLBAR_CALLBROWSER1_ACTIONS<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_TYPE<br /><br /> IDG_VS_TOOLBAR_CALLBROWSER1_CBSETTINGS|
|중단점|guidVSDebugGroup:IDM_BREAKPOINTS_WINDOW_TOOLBAR|IDG_BREAKPOINTS_WINDOW_NEW<br /><br /> IDG_BREAKPOINTS_WINDOW_DELETE<br /><br /> IDG_BREAKPOINTS_WINDOW_ALL<br /><br /> IDG_BREAKPOINTS_WINDOW_VIEW<br /><br /> IDG_BREAKPOINTS_WINDOW_EDIT<br /><br /> IDG_BREAKPOINTS_WINDOW_COLUMNS|
|디스어셈블리|guidVSDebugGroup:IDM_DISASM_WINDOW_TOOLBAR|IDG_DISASM_WINDOW_TOOLBAR|
|1-4 메모리|guidVSDebugGroup:IDM_MEMORY_WINDOW_TOOLBAR1...4|IDG_MEMORY_EXPRESSION1..4<br /><br /> IDG_MEMORY_COLUMNS1..4|
|프로세스|guidVSDebugGroup:IDM_ATTACHED_PROCS_TOOLBAR|IDG_ATTACHED_PROCS_EXECCNTRL IDG_ATTACHED_PROCS_STEPPING<br /><br /> IDG_ATTACHED_PROCS_EXECCNTRL2<br /><br /> IDG_ATTACHED_PROCS_ATTACH<br /><br /> IDG_ATTACHED_PROCS_COLUMNS|

## <a name="see-also"></a>참고자료
- [도구 모음에 메뉴 컨트롤러 추가](../../extensibility/adding-a-menu-controller-to-a-toolbar.md)
- [도구 창에 도구 모음을 추가 합니다.](../../extensibility/adding-a-toolbar-to-a-tool-window.md)
- [Guid 및 Id의 Visual Studio 메뉴](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)