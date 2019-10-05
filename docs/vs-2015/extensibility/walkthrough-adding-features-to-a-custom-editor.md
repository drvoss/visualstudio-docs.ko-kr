---
title: '연습: 추가 기능을 사용자 지정 편집기에 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d14fb36298518409df34302f9346e186f0b0263
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825160"
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>연습: 사용자 지정 편집기에 기능 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 지정 편집기를 만든 후에 더 많은 기능을 추가할 수 있습니다.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>VSPackage에 대 한 편집기를 만들려면  
  
1. Visual Studio 패키지 프로젝트 템플릿을 사용 하 여 사용자 지정 편집기를 만듭니다.  
  
     자세한 내용은 [연습: 사용자 지정 편집기 만들기](../extensibility/walkthrough-creating-a-custom-editor.md)합니다.  
  
2. 편집기는 단일 또는 여러 개의 뷰를 지원 하도록 할지 여부를 결정 합니다.  
  
     지 원하는 편집기를 **새 창** 명령을 또는 폼 보기와 코드 보기에는 별도 문서 데이터 개체 및 문서 보기 개체가 필요 합니다. 하나의 뷰만 지 원하는 편집기에서 문서 데이터 개체 및 문서 보기 개체 동일한 개체에서 구현할 수 있습니다.  
  
     여러 뷰 예제를 보려면 [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md)합니다.  
  
3. 편집기 팩터리를 구현 하 여 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> 인터페이스입니다.  
  
     자세한 내용은 [편집기 팩터리](../extensibility/editor-factories.md)합니다.  
  
4. 내부 활성화를 사용 하 여 편집기를 원 하거나 간단한 문서 보기 개체 창 관리를 포함 하는지 여부를 결정 합니다.  
  
     간단한 포함 편집기 창 ActiveX 컨트롤 또는 다른 활성 문서 뷰 개체로 바로 활성화 편집기 창을 호스트 하는 동안 표준 문서 뷰를 호스팅합니다. 자세한 내용은 참조 하세요. [포함 간체](../extensibility/simplified-embedding.md) 하 고 [내부 활성화](../misc/in-place-activation.md)합니다.  
  
5. 구현 된 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 명령을 처리 하는 인터페이스입니다.  
  
6. 다음을 수행 하 여 문서 지 속성 및 외부 파일 변경 내용에 대 한 응답을 제공 합니다.  
  
    1. 파일을 유지 하려면 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> 편집기의 문서 데이터 개체입니다.  
  
    2. 외부 파일 변경 내용에 응답 하려면 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> 고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> 편집기의 문서 데이터 개체입니다.  
  
        > [!NOTE]
        > 호출 `QueryService` 대 <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> 에 대 한 포인터를 가져오려면 `IVsFileChangeEx`합니다.  
  
7. 소스 코드 제어를 사용 하 여 문서 편집 이벤트를 조정 합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면  
  
    1. 포인터를 가져옵니다 `IVsQueryEditQuerySave2` 호출한 `QueryService` 에서 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>합니다.  
  
    2. 첫 번째 편집 이벤트가 발생할 때 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 메서드.  
  
         파일을 체크 아웃 아직 선택 하지 않은 경우 사용자 라는 메시지를 표시 합니다. 오류를 방지 하는 "파일을 체크 아웃 되지 않으므로" 조건을 처리 해야 합니다.  
  
    3. 마찬가지로, 파일을 저장 하기 전에 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> 메서드.  
  
         이 메서드 저장 되지 않은 경우 또는 마지막 저장 이후 변경 된 경우 파일을 저장 하 라는 메시지입니다.  
  
8. 사용 하도록 설정 합니다 **속성** 창 편집기에서 선택한 텍스트에 대 한 속성을 표시 합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면  
  
    1. 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 각 시간 텍스트 선택 영역이 변경, 전달 구현의 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>합니다.  
  
    2. 호출 `QueryService` 대 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 에 대 한 포인터를 가져오기 위해 서비스 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>합니다.  
  
9. 편집기 간에 항목을 끌어서 수 있도록 하며 **도구 상자**, 간이나 외부 편집기 (예: Microsoft Word) 및 **도구 상자**합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면  
  
    1. 구현 `IDropTarget` 경고 IDE 편집기는 놓기 대상으로 하는 편집기에서.  
  
    2. 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> 뷰 편집기를 사용 하도록 설정 하 고에서 항목을 사용 하지 않도록 설정할 수 있도록 인터페이스를 **도구 상자**.  
  
    3. 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> 호출 `QueryService` 온 <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> 에 대 한 포인터를 사용 하려면이 서비스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> 및 <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> 인터페이스.  
  
         이렇게 하면 새 항목을 추가 하 여 VSPackage를 **도구 상자**합니다.  
  
10. 편집기에 대 한 다른 선택적 기능 하는지 여부를 결정 합니다.  
  
    - 편집기 지원 하도록 하려는 경우 찾기 및 바꾸기 명령, 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>합니다.  
  
    - 편집기에서 문서 개요 도구 창을 사용 하려는 경우 구현 `IVsDocOutlineProvider`합니다.  
  
    - 편집기에서 상태 표시줄을 사용 하려는 경우 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> 호출 `QueryService` 에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> 에 대 한 포인터를 가져오려면 `IVsStatusBar`합니다.  
  
         편집기에서 줄을 표시할 수는 예를 들어 / 열 정보, 선택 모드 (스트림 / 상자) 및 삽입 모드 (삽입 / 겹쳐서 표시).  
  
    - 편집기 지원 하도록 하려는 경우는 `Undo` 명령을 OLE 실행 취소 관리자 모델을 사용 하는 것이 좋습니다. 대신 편집기 핸들을 할 수 있습니다는 `Undo` 직접 명령입니다.  
  
11. VSPackage, 메뉴, 편집기 및 기타 기능에 대 한 Guid를 비롯 한 내용은 레지스트리를 만듭니다.  
  
     다음은 일반적인 예는 코드 편집기를 제대로 등록 하는 방법을 보여 주기 위해.rgs 파일 스크립트에 놓기만 하면 됩니다.  
  
    ```  
    NoRemove Editors  
    {  
          ForceRemove {...guidEditor...} = s 'RTF Editor'  
          {  
             val Package = s '{...guidVsPackage...}'  
             ForceRemove Extensions  
             {  
                val rtf = d 50  
             }  
          }  
    }  
    NoRemove Menus  
    {  
          val {...guidVsPackage...} = s ',203,11'  
    }  
    ```  
  
12. 상황에 맞는 도움말 지원을 구현 합니다.  
  
     이렇게 하면 F1 도움말과 동적 도움말 창 편집기에서 항목에 대 한 지원을 제공할 수 있습니다. 이 대 한 자세한 내용은 참조 하세요. [방법: 편집기에 대 한 컨텍스트를 제공](../extensibility/how-to-provide-context-for-editors.md)합니다.  
  
13. 편집기에서 자동화 개체 모델을 구현 하 여 노출 된 `IDispatch` 인터페이스입니다.  
  
     자세한 내용은 [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md)을 참조하세요.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
  
- IDE를 호출 하는 경우 편집기 인스턴스가 만들어질는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 메서드. 편집기에는 여러 뷰를 지 원하는 경우 `CreateEditorInstance` 문서 데이터와 문서 뷰 개체를 만듭니다. 문서 데이터 개체가 이미 있으면 열에 null이 아닌 `punkDocDataExisting` 값이 전달 `IVsEditorFactory::CreateEditorInstance`합니다. 편집기 팩터리 구현에 적절 한 인터페이스에 대 한 쿼리를 통해 기존 문서 데이터 개체를 호환 되는지 여부를 결정 해야 합니다. 자세한 내용은 [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md)합니다.  
  
- 간단한 포함 방법을 사용할 경우 구현 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 인터페이스입니다.  
  
- 내부 활성화를 사용 하려는 경우에 다음 인터페이스를 구현 합니다.  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    > `IOleInPlaceComponent` 인터페이스 OLE 2 메뉴 병합 방지를 사용 합니다.  
  
     프로그램 `IOleCommandTarget` 구현을 처리 명령 등 **잘라내기**를 **복사**, 및 **붙여넣기**합니다. 구현 하는 경우 `IOleCommandTarget`에서 정의한 표준 명령을 구현할 수 있는 경우 또는 편집기 자체 명령 메뉴 구조를 정의 하는 고유한.vsct 파일을 필요한 지 여부를 결정 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다. 일반적으로 편집기 및 IDE의 메뉴를 확장 하며 사용 자신의 도구 모음을 정의 합니다. 그러나 자주 필요는 IDE의 표준 명령 집합을 사용 하는 것 외에도 고유한 특정 명령을 정의 하는 편집기에 대 한 합니다. 이렇게 하려면 편집기 사용 하며 다음.vsct 파일에서 새 명령, 상황에 맞는 메뉴를 최상위 메뉴 및 도구 모음을 정의 하는 일반적인 명령 선언 해야 합니다. 내부 활성화 편집기를 만드는 경우 다음 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> OLE 2 메뉴 병합을 사용 하는 대신.vsct 파일의 편집기에 대 한 메뉴 및 도구 모음을 정의 합니다.  
  
- 메뉴 명령 UI에서가 중 시키는 방지 하려면 새 명령을 고안 하기 전에 IDE에서 기존 명령을 사용 해야 있습니다. 공유 명령 SharedCmdDef.vsct ShellCmdDef.vsct에 정의 됩니다. 이러한 파일의 VisualStudioIntegration\Common\Inc 하위 디렉터리에 기본적으로 설치 된 프로그램 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 설치 합니다.  
  
- `ISelectionContainer` 단일 및 다중 선택 항목을 표현할 수 있습니다. 선택한 각 개체도 구현 되는 `IDispatch` 개체입니다.  
  
- IDE 구현 `IOleUndoManager` 에서 액세스할 수 있는 서비스로 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> 또는 통해 인스턴스화할 수 있는 개체로 <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>합니다. 편집기 구현 하는 `IOleUndoUnit` 각각에 대 한 인터페이스 `Undo` 작업 합니다.  
  
- 두 위치는 사용자 지정 편집기 자동화 개체를 노출할 수 있습니다.  
  
  - `Document.Object`  

  - `Window.Object`  
  
## <a name="see-also"></a>관련 항목  
 [자동화 모델에 영향을 주는](../extensibility/internals/contributing-to-the-automation-model.md)   
 [방법: 편집기의 컨텍스트 제공](../extensibility/how-to-provide-context-for-editors.md)
