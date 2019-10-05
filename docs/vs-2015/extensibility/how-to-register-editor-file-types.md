---
title: '방법: 편집기 파일 형식 등록 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204113"
---
# <a name="how-to-register-editor-file-types"></a>방법: 편집기 파일 형식 등록
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

일부분으로 제공 하는 등록 특성을 사용 하 여 편집기 파일 형식을 등록 하는 가장 쉬운 방법은는 [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 관리 되는 패키지 프레임 워크 (MPF) 클래스입니다. 네이티브에서 패키지를 구현 하는 경우 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], 편집기 및 연결 된 확장을 등록 하는 레지스트리 스크립트를 작성할 수도 있습니다.  
  
## <a name="registration-using-mpf-classes"></a>MPF 클래스를 사용 하 여 등록  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>MPF 클래스를 사용 하 여 편집기 파일 형식 등록  
  
1. 제공 된 <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> VSPackage의 클래스에 편집기에 대 한 적절 한 매개 변수를 사용 하 여 클래스입니다.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     여기서 "입니다. "샘플은이 편집기에 등록 된 확장 이며"32"우선 순위 수준입니다.  
  
     합니다 `projectGuid` 에 정의 된 기타 파일 형식에 대 한 guid <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>합니다. 결과 파일은 빌드 프로세스의 일부가 되도록 하지 있도록 기타 파일 형식이 제공 됩니다.  
  
     `TemplateDir` 관리 되는 기본 편집기 샘플에 포함 되어 있는 템플릿 파일이 포함 된 폴더를 나타냅니다.  
  
     `NameResourceID` BasicEditorUI 프로젝트의 Resources.h 파일에 정의 하 고 "내 Editor" 서의 편집기를 식별 합니다.  
  
2. <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드를 재정의합니다.  
  
     구현에서는 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> 메서드와으로 편집기 팩터리의 인스턴스 아래에서 설명 하는 전달 합니다.  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     이 단계는 편집기 팩터리와 편집기 파일 확장명을 등록합니다.  
  
3. 편집기 팩터리를 등록 취소 합니다.  
  
     편집기 팩터리 VSPackage 삭제 될 때 자동으로 등록 된지 않습니다. 편집기 팩터리 개체 구현 하는 경우는 <xref:System.IDisposable> 인터페이스를 해당 `Dispose` 팩터리를 등록을 취소 한 후 메서드는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]합니다.  
  
## <a name="registration-using-a-registry-script"></a>레지스트리 스크립트를 사용 하 여 등록  
 네이티브에서 파일 형식과 편집기 팩터리를 등록 [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] 이루어집니다 다음에 설명 된 대로 windows 레지스트리에 쓸 레지스트리 스크립트를 사용 하 합니다.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>레지스트리 스크립트를 사용 하 여 편집기 파일 형식 등록  
  
1. 레지스트리 스크립트에서 정의 편집기 팩터리 및 편집기 팩터리의 GUID 문자열에 표시 된 대로 `GUID_BscEditorFactory` 다음 레지스트리 스크립트의 섹션입니다. 또한 확장 및 편집기 확장의 우선 순위를 정의 합니다.  
  
    ```  
  
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions            {                val rtf = d 50            }  
        }  
    }  
    ```  
  
     이 예에서 편집기 파일 확장명은 ".rtf"로 식별 되며 해당 우선 순위 "50". GUID 문자열 BscEdit 샘플 프로젝트의 Resource.h 파일에 정의 됩니다.  
  
2. VSPackage를 등록 합니다.  
  
3. 편집기 팩터리를 등록 합니다.  
  
     편집기 팩터리에 등록 되는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> 구현 합니다.  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     GUID 문자열 BscEdit 프로젝트의 Resource.h 파일에 정의 됩니다.
