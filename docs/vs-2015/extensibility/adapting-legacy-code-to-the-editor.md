---
title: 레거시 코드 편집기로 적응 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapters
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb90723a72c10dbf6cfda5edd4aa68f71f1c6b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184912"
---
# <a name="adapting-legacy-code-to-the-editor"></a>레거시 코드를 편집기로 조정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 편집기에 기존 코드 구성 요소에서 액세스할 수 있는 많은 기능이 있습니다. 다음 지침을 예를 들어 VSPackage로 편집기 기능을 사용 하려면-MEF 구성 요소를 조정 하는 방법을 보여 줍니다. 지침에는 서비스를 가져올 편집기의 관리 및 비관리 코드에서 어댑터를 사용 하는 방법을 보여 줍니다.  
  
## <a name="editor-adapters"></a>편집기 어댑터  
 편집기 어댑터나, shim은 또한 클래스 및 인터페이스를 노출 하는 편집기 개체에 대 한 래퍼를 <xref:Microsoft.VisualStudio.TextManager.Interop> API. 예를 들어 비 편집기 서비스 간에 이동 하려면 어댑터, Visual Studio 셸 명령 및 편집기 서비스를 사용할 수 있습니다. (이 경우 Visual Studio의 편집기를 현재 호스트 되는 방법) 어댑터는 또한 Visual Studio에서 제대로 작동 하려면 레거시 편집기 및 언어 서비스 확장을 사용 합니다.  
  
## <a name="using-editor-adapters"></a>편집기 어댑터를 사용 하 여  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> 새 편집기 인터페이스 및 레거시 인터페이스를 전환 하는 메서드 및 어댑터를 만드는 메서드를 제공 합니다.  
  
 이 서비스는 MEF 구성 요소 파트를 사용 하는 경우 다음과 같은 서비스를 가져올 수 있습니다.  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 비-MEF 구성 요소에서이 서비스를 사용 하려는 경우이 항목의 뒷부분에 나오는 "를 사용 하 여 Visual Studio 편집기 서비스는 비-MEF 구성 요소" 섹션의 지침을 따릅니다.  
  
## <a name="switching-between-the-new-editor-api-and-the-legacy-api"></a>새 편집기 API와 레거시 API 간의 전환  
 편집기 개체 및 레거시 인터페이스를 전환 하려면 다음 메서드를 사용 합니다.  
  
|메서드|변환|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|변환를 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>합니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|변환를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 에 <xref:Microsoft.VisualStudio.Text.ITextBuffer>합니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|변환를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 에 <xref:Microsoft.VisualStudio.Text.ITextBuffer>합니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|변환를 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>합니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|변환를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 에 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>합니다.|  
  
## <a name="creating-adapters"></a>어댑터 만들기  
 레거시 인터페이스에 대 한 어댑터를 만들려면 다음 메서드를 사용 합니다.  
  
|메서드|변환|  
|------------|----------------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>를 만듭니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|만듭니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 지정 된 <xref:Microsoft.VisualStudio.Utilities.IContentType>합니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>를 만듭니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>를 만듭니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|만듭니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 에 대 한는 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>합니다.|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>를 만듭니다.|  
  
## <a name="creating-adapters-in-unmanaged-code"></a>관리 되지 않는 코드에서 어댑터를 만드는 방법  
 모든 어댑터 클래스를 로컬로 등록 된 공동 creatable를 사용 하 여 인스턴스화할 수는 `VsLocalCreateInstance()` 함수입니다.  
  
 모든 어댑터에서 vsshlids.h 파일에 정의 된 Guid를 사용 하 여 만들어진 합니다... Visual Studio SDK 설치의 \VisualStudioIntegration\Common\Inc\ 폴더입니다. VsTextBufferAdapter의 인스턴스를 만들려면 다음 코드를 사용 합니다.  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## <a name="creating-adapters-in-managed-code"></a>관리 코드에서 어댑터 만들기  
 관리 코드에서 비관리 코드에서 설명한 것과 동일한 방식으로 어댑터를 함께 만들 수 있습니다. 또한 만들고 어댑터와 상호 작용할 수 있도록 MEF 서비스를 사용할 수 있습니다. 이러한 방식으로 어댑터를 공동으로 만들 때 보다 더 세밀 하 게 제어할 수 있습니다.  
  
#### <a name="to-create-an-adapter-for-ivstextview"></a>IVsTextView에 대 한 어댑터를 만들려면  
  
1. Microsoft.VisualStudio.Editor.dll에 대 한 참조를 추가 합니다. 했는지 `CopyLocal` 로 설정 된 `false`합니다.  
  
2. 인스턴스화하는 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>다음과 같이 합니다.  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3. `CreateX()` 메서드를 호출합니다.  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## <a name="using-the-visual-studio-editor-directly-from-unmanaged-code"></a>관리 되지 않는 코드에서 직접 Visual Studio 편집기를 사용 하 여  
 Microsoft.VisualStudio.Platform.VSEditor 네임 스페이스 및 Microsoft.VisualStudio.Platform.VSEditor.Interop 네임 스페이스를 IVx 인터페이스로 COM 호출 가능 인터페이스를 노출합니다. 예를 들어 Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer 인터페이스는 COM 버전의는 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 인터페이스입니다. `IVxTextBuffer`, 버퍼 스냅숏에 액세스, 버퍼를 수정, 수신 버퍼의 텍스트 변경 이벤트에 대 한 고 추적 지점 및 범위를 만들 수 있습니다. 다음 단계에서는 액세스 하는 방법을 보여는 `IVxTextBuffer` 에서 `IVsTextBuffer`합니다.  
  
#### <a name="to-get-an-ivxtextbuffer"></a>IVxTextBuffer를 가져오려면  
  
1. IVx* 인터페이스에 대 한 정의에 VSEditor.h 파일에 포함 되는... Visual Studio SDK 설치의 \VisualStudioIntegration\Common\Inc\ 폴더입니다.  
  
2. 다음 코드를 사용 하 여 텍스트 버퍼를 인스턴스화하는 `IVsUserData->GetData()` 메서드. 다음 코드에서는 `pData` 에 대 한 포인터를 `IVsUserData` 개체입니다.  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## <a name="using-visual-studio-editor-services-in-a-non-mef-component"></a>Visual Studio 편집기 서비스를 사용 하 여 비-MEF 구성 요소  
 MEF를 사용 하지 않는 기존 관리 되는 코드 구성 요소 있고 Visual Studio 편집기의 서비스를 사용 하려는 경우 ComponentModelHost VSPackage를 포함 하는 어셈블리에 대 한 참조를 추가 하 고 해당 SComponentModel 서비스 가져오기 해야 합니다.  
  
#### <a name="to-consume-visual-studio-editor-components-from-a-non-mef-component"></a>비-MEF 구성 요소에서 Visual Studio 편집기 구성 요소를 사용 하려면  
  
1. Microsoft.VisualStudio.ComponentModelHost.dll 어셈블리에 대 한 참조를 추가 합니다... Visual Studio 설치의 \Common7\IDE\ 폴더입니다. 했는지 `CopyLocal` 로 설정 된 `false`합니다.  
  
2. 개인 추가 `IComponentModel` Visual Studio 편집기 서비스를 다음과 같이 사용 하려는 클래스 멤버입니다.  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3. 구성 요소에 대 한 초기화 메서드에서 구성 요소 모델을 인스턴스화하십시오.  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4. 그런 다음 Visual Studio 편집기 서비스 중 하나를 호출 하 여 가져올 수 있습니다는 `IComponentModel.GetService<T>()` 원하는 서비스에 대 한 메서드.  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```
