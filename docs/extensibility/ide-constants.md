---
title: IDE 상수 | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d16b758a34eb1b9f48e912f75c4eec144a07ce4a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311324"
---
# <a name="ide-constants"></a>IDE 상수

<xref:Microsoft.VisualStudio.VSConstants> 클래스는 통합된 개발 환경 (IDE)에 관련 된 헤더 파일에만 이전에 정의 된 있고 상수를 제공 합니다.

## <a name="logical-and-physical-views"></a>논리적 및 물리적 보기

|값|설명|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 이 값을 전달 해야 하는 처리기를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드를 합니다 **연결** 가능한 코드 보기에이 경우에서 대화 상자.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 이 값을 전달 하는 처리기를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드를 합니다 **연결** 대화 상자,이 경우 가능한 채워집니다 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> 디버깅으로 동일한 보기에 매핑되는 뷰 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 이 값을 전달 하는 처리기를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드를를 **연결** 대화 상자에이 예제의 **양식 보기** 디자이너 뷰.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 이 값을 전달 하는 처리기를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드를 합니다 **연결 프로그램** 편집기 팩터리의 기본/기본 보기의 경우이 대화 상자에서.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 이 값을 전달 하는 처리기를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드를 합니다 **연결 프로그램** 텍스트 편집기 보기로 문서 또는 데이터에 대 한이 대화 상자에서.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 이 값을 전달 하는 처리기는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메서드를 사용 하는 사용자 정의 뷰를 선택 하 라는 메시지입니다.|

## <a name="editor-factory-flags"></a>편집기 팩터리 플래그

|값|설명|
|-----------|-----------------|
|[CEF.CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|사용 되지 않는 플래그 비트의 첫 번째 매개 변수로 결합 된 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 메서드.|
|[CEF.OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|첫 번째 매개 변수로 비트 결합을 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, 메서드를 나타냅니다 편집기 팩터리 필요한 수정 프로그램을 수행 해야 합니다.|
|[CEF.OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|첫 번째 매개 변수로 비트 결합을 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 메서드를이 플래그는 상호 배타적 이며 [CEF입니다. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)합니다.|
|[CEF.Silent](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|첫 번째 매개 변수로 비트 결합을 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 메서드를 나타냅니다 (UI) 사용자 인터페이스를 표시 하지 않고 편집기 팩터리 편집기를 만들어야 합니다.|

## <a name="visual-studio-errors"></a>Visual Studio 오류

|값|설명|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|비동기 동작 인터페이스에서 반환 된 상수 때 해당 개체에서 이미 사용 중|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|"호환 되지 않는 문서 데이터"에 대 한 Visual Studio에 관련 된 HRESULT 오류입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Visual Studio와 관련 된 HRESULT 오류가 나타냅니다 "패키지를 로드 되지 않았습니다."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Visual Studio와 관련 된 HRESULT 오류가 발생 함을 "프로젝트가 이미 있습니다."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Visual Studio에 국한 되며 "프로젝트 구성에 실패 했습니다."를 나타내는 HRESULT 오류가 발생|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Visual Studio와 관련 된 HRESULT 오류가 나타냅니다 "프로젝트가 로드 되지 않습니다."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Visual Studio와 관련 된 HRESULT 오류가 나타냅니다 "솔루션 이미 열려 있습니다."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Visual Studio에 국한 되며 "솔루션을 열지."를 나타내는 HRESULT 오류가 발생|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|배열에서 지정 하는 매개 변수가 있는 빌드 인터페이스에서 반환 되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> 인터페이스 하지만 구현만 적용할 수 있습니다 메서드가 모든 출력 합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 메서드 문서 편집기에서 열 수 없는 형식에 있으면이 값을 반환 합니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|사용자는 Visual Studio 마법사에서 뒤로 단추 적중 나타냅니다는 HRESULT 값입니다.|

## <a name="visual-studio-constants"></a>Visual Studio 상수

|값|설명|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Visual Studio와 관련 된 HRESULT 오류가 나타냅니다 "프로젝트를 전달 합니다."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|"도구 상자 표식입니다."에 대 한 Visual Studio에 관련 된 상수|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|통해 알림 메시지를 위해 Visual Studio에 관련 된 상수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 메서드 모달의 시작을 나타냅니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|통해 알림 메시지를 위해 Visual Studio에 관련 된 상수는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 모달의 끝을 나타내는 방법입니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|통해 알림 메시지를 위해 Visual Studio에 관련 된 상수를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 메서드를 나타내는 명령 모음 메트릭을 변경 되었습니다.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|쿠키 설정 되어 있지 않음을 나타내는 Visual Studio에 해당 되는 상수입니다.|
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|프로젝트 항목의 없음을 나타내는 Visual Studio 항목 식별자입니다. 이 값은 현재 선택 영역이 없는 경우 사용 됩니다.|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|프로젝트 계층의 루트를 나타내는 단일 항목 대신 전체 계층 구조를 식별 하기 위해 사용 하는 Visual Studio 항목 식별자입니다.|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|현재 선택된 된 항목 또는 계층의 루트를 포함할 수 있는 항목을 나타내는 Visual Studio 항목 식별자입니다.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 IDE의 구성 요소는 무엇입니까을 방금 선택한 후에 설명는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> 예를 들어를 호출 합니다.

|상수|값|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 새 선택 상태를 나타내는 데 사용 하는 상수입니다.

|상수|값|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>구성 요소 선택기 대화 상수

|상수|값|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>참고자료

- [프로젝트 시스템 확장을 위한 IDE 정의 명령](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)