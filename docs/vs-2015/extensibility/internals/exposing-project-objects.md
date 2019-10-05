---
title: 프로젝트 개체 노출 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f40c523c058bf215cc4574b3aa4a2e038c833beb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196649"
---
# <a name="exposing-project-objects"></a>프로젝트 개체 노출
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트 형식 사용자 지정 자동화 인터페이스를 사용 하 여 프로젝트에 대 한 액세스를 허용 하려면 자동화 개체를 제공할 수 있습니다. 모든 프로젝트 형식 표준 제공할 예정입니다 <xref:EnvDTE.Project> 에서 액세스 되는 자동화 개체 <xref:EnvDTE.Solution>, IDE에서 열려 있는 모든 프로젝트의 컬렉션이 들어 있는입니다. 프로젝트의 각 항목에 의해 노출 되 될를 <xref:EnvDTE.ProjectItem> 개체를 사용 하 여 액세스할 <xref:EnvDTE.Project.ProjectItems>합니다. 이러한 표준 automation 개체 외에도 프로젝트 프로젝트 관련 자동화 개체를 제공할 수 있습니다.  
  
 사용자 지정 루트 수준의 자동화 하는 개체에 액세스할 수 있습니다 사용 하 여 루트 DTE 개체에서 바인딩된을 만들 수 있습니다 `DTE.<customeObjectName>` 또는 `DTE.GetObject(“<customObjectName>”)`합니다. 예를 들어 Visual C++ 만듭니다 C++ 프로젝트 관련 프로젝트 컬렉션 DTE를 사용 하 여 액세스할 수 있는 "VCProjects"를 호출 합니다. VCProjects 또는 DTE 합니다. GetObject("VCProjects") 합니다. 또한는 Project.CodeModel ProjectItem.Object 및 ProjectItem.FileCodeModel를 노출 하는 프로젝트 항목, 가장 많이 파생 된 개체에 대 한 쿼리 될 수 있는 프로젝트 형식에 대해 고유한 Project.Object를 만들 수 있습니다.  
  
 사용자 지정, 프로젝트별 프로젝트 컬렉션을 노출 하는 프로젝트에 대 한 일반적인 규칙은 예를 들어 [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 만듭니다는 C++ 특정 프로젝트 컬렉션을 사용 하 여 액세스할 수 있습니다 `DTE.VCProjects` 하거나 `DTE.GetObject("VCProjects")`합니다. 만들 수도 있습니다는 `Project.Object`, 프로젝트 형식에 대 한 고유한를 `Project.CodeModel`, 가장 많이 파생 된 개체를 쿼리할 수 있는 `ProjectItem`를 노출 하는 `ProjectItem.Object`, 및 `ProjectItem.FileCodeModel`.  
  
### <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>프로젝트를 VSPackage-지정 된 개체에 적용할  
  
1. VSPackage의.pkgdef 파일에 적절 한 키를 추가 합니다.  
  
     예를 들어, 다음은.pkgdef 설정에 대 한는 C++ 언어 프로젝트:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]  
    "VCProjects"=""  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]  
    "VCProjectEngineEventsObject"=""  
    ```  
  
2. 코드를 구현 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 메서드를 다음 예제와 같이 합니다.  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject(  
    /* [in]  */ LPCOLESTR       pszPropName,   
    /* [out] */ IDispatch **    ppIDispatch)  
    {  
    ExpectedPtrRet(pszPropName);  
    ExpectedPtrRet(ppIDispatch);  
    *ppIDispatch = NULL;  
  
        if (m_fZombie)  
            return E_UNEXPECTED;  
  
        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)  
        {  
            return GetAutomationProjects(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)  
        {  
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);  
        }  
        return E_INVALIDARG;  
    }   
    ```  
  
     코드에서 `g_wszAutomationProjects` 프로젝트 컬렉션의 이름입니다. `GetAutomationProjects` 메서드를 구현 하는 개체를 만듭니다를 `Projects` 인터페이스와 반환은 `IDispatch` 에 다음 코드 예제와 같이 호출 하는 개체에 대 한 포인터입니다.  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)  
    {  
        ExpectedPtrRet(ppIDispatch);  
        *ppIDispatch = NULL;  
  
        if (!m_srpAutomationProjects)  
        {  
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);  
            IfFailRet(hr);  
            ExpectedExprRet(m_srpAutomationProjects != NULL);  
        }  
        return m_srpAutomationProjects.CopyTo(ppIDispatch);  
    }  
    ```  
  
     자동화 개체에 대 한 고유한 이름을 선택 해야 합니다. 이름 충돌 예측 가능 하지 않으며 충돌 하면 임의로 발생 여러 프로젝트 형식에 동일한 이름을 사용 하는 충돌 하는 개체 이름입니다. 회사 이름 또는 해당 제품 이름 자동화 개체의 고유 일부를 포함 해야 합니다.  
  
     사용자 지정 `Projects` 컬렉션 개체는 프로젝트 자동화 모델의 나머지 부분에 대 한 편의 진입점입니다. 프로젝트 개체에서 액세스할 수 이기도 합니다 <xref:EnvDTE.Solution> 프로젝트 컬렉션입니다. 사용 하 여 소비자에 게 제공 하는 적절 한 코드 및 레지스트리 항목을 만든 후 `Projects` 컬렉션 개체에 남아 있는 프로젝트 모델에 대 한 표준 개체 구현을 제공 해야 합니다. 자세한 내용은 [프로젝트 모델링](../../extensibility/internals/project-modeling.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
