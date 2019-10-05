---
title: '방법: 기본 제공 글꼴 및 색 구성표에 액세스 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685315"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>방법: 기본 제공 글꼴 및 색 구성표에 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 통합된 개발 환경 (IDE) 편집기 창과 사용 하 여 연결 된 글꼴 및 색 구성표를 있습니다. 이 체계를 통해 액세스할 수 있습니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 인터페이스입니다.  
  
 기본 제공 글꼴 및 색 구성표를 사용 하려면 VSPackage 수행 해야 합니다.  
  
- 기본 글꼴 및 색 서비스를 사용 하는 범주를 정의 합니다.  
  
- 기본 글꼴 및 색 서버를 사용 하 여 범주를 등록 합니다.  
  
- 특정 창에서는 기본 제공 항목 및 범주를 사용 하 여 IDE를 권장 합니다 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` 및 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` 인터페이스입니다.  
  
  IDE 창에 결과 범주를 사용합니다. 범주 이름이 표시 됩니다는 **설정 표시:** 드롭다운 목록 상자에는 **글꼴 및 색** 속성 페이지.  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>기본 제공 글꼴 및 색을 사용 하 여 범주를 정의 하려면  
  
1. 임의의 GUID를 만듭니다.  
  
    이 GUID는 범주를 고유 하 게 식별 하는 데 사용 됩니다<strong>합니다.</strong> 이 범주는 IDE의 기본 글꼴 및 색 지정을 재사용합니다.  
  
   > [!NOTE]
   > 사용 하 여 글꼴 및 색 데이터를 검색 하는 경우는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> 다른 인터페이스를 Vspackage를 사용 하 여이 GUID 기본 제공 정보를 참조 합니다.  
  
2. 범주 이름은 IDE에서 표시 하는 경우 필요에 따라 지역화 될 수 있도록 VSPackage의 리소스 (.rc) 파일 내에서 문자열 테이블에 추가 되어야 합니다.  
  
    자세한 내용은 [추가 또는 삭제 하는 문자열](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab)합니다.  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>기본 제공 글꼴 및 색을 사용 하 여 범주를 등록 하려면  
  
1. 특수 한 유형의 다음 위치에 레지스트리 항목 범주를 생성 합니다.  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio version>* \FontAndColors\\*\<Category>*]  
  
     *\<범주 >* 범주의 지역화 되지 않은 이름입니다.  
  
2. 4 개의 값이 포함 된 스톡 글꼴 및 색 구성표를 사용 하도록 레지스트리를를 채웁니다.  
  
    |이름|형식|데이터|설명|  
    |----------|----------|----------|-----------------|  
    |범주|REG_SZ|GUID|스톡 글꼴 및 색 구성표를 포함 하는 범주를 식별 하는 임의의 GUID입니다.|  
    |Package|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> 이 GUID는 기본 글꼴 및 색 구성을 사용 하는 모든 Vspackage에서 사용 됩니다.|  
    |NameID|REG_DWORD|ID|리소스의 ID는 VSPackage에서 지역화할 수 있는 범주 이름입니다.|  
    |ToolWindowPackage|REG_SZ|GUID|구현 하는 VSPackage의 GUID는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 인터페이스입니다.|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>시스템 제공 글꼴 및 색 사용을 시작 하려면  
  
1. 인스턴스를 만듭니다는 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` 창의 구현과 초기화의 일부로 인터페이스입니다.  
  
2. 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> 의 인스턴스를 가져올 방법 합니다 `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` 현재 해당 인터페이스 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 인스턴스.  
  
3. 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> 두 번입니다.  
  
   - 사용 하 여 한 번 호출 `VSEDITPROPID_ViewGeneral_ColorCategory`인수로 합니다.  
  
   - 사용 하 여 한 번 호출 `VSEDITPROPID_ViewGeneral_FontCategory` 인수로 합니다.  
  
     이 설정 하 고 창의 속성으로는 기본 글꼴 및 색 서비스를 제공 합니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 기본 제공 글꼴 및 색 사용을 시작합니다.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [글꼴 및 색을 사용 하 여](../extensibility/using-fonts-and-colors.md)   
 [글꼴 및 텍스트 색 지정에 대 한 색 정보 가져오기](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [저장 된 글꼴 및 색 설정에 액세스](../extensibility/accessing-stored-font-and-color-settings.md)   
 [글꼴 및 색 개요](../extensibility/font-and-color-overview.md)
