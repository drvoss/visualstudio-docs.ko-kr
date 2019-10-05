---
title: 레거시 API를 사용 하 여 보기 설정 변경 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7d58d1477b9d7f58242f8cb4db7c3c360c248b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68184473"
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>레거시 API를 사용하여 보기 설정 변경
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

가상 공간, 자동 줄 바꿈 및 선택 영역 여백 등의 핵심 편집기 기능에 대 한 설정을 이용 하 여 사용자가 변경할 수 있습니다 합니다 **옵션** 대화 상자. 하지만 이러한 설정을 변경할 수 이기도 프로그래밍 방식으로 합니다.  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>레거시 API를 사용 하 여 설정 변경  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> 인터페이스는 텍스트 편집기 속성 집합을 노출 합니다. 텍스트 뷰의 텍스트 보기에 대 한 프로그래밍 방식으로 변경 된 설정 그룹을 나타내는 속성 (GUID_EditPropCategory_View_MasterSettings)의 범주를 포함 합니다. 이 방식으로 뷰 설정이 변경 된 후에 변경할 수 없습니다는 **옵션** 재설정 하기 전에 대화 상자.  
  
 다음은 핵심 편집기 인스턴스에 대 한 보기 설정을 변경 하기 위한 일반적인 프로세스입니다.  
  
1. 호출 `QueryInterface` 에 (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>)에 대 한는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> 인터페이스입니다.  
  
2. 호출 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> GUID_EditPropCategory_View_MasterSettings에 대 한 값을 지정 하는 메서드를는 `rguidCategory` 매개 변수입니다.  
  
     이렇게에 대 한 포인터를 반환 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> 인터페이스 뷰에 대 한 강제 속성 집합이 포함 되어 있습니다. 이 그룹의 모든 설정이 영구적으로 강제로 적용 합니다. 설정이이 그룹에 없는 경우 지정 된 옵션 따릅니다 합니다 **옵션** 대화 상자 또는 사용자의 명령을 합니다.  
  
3. 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> 메서드에 적절 한 설정 값을 지정 하는 `idprop` 매개 변수입니다.  
  
     예를 들어, 자동 줄 바꿈을 강제 적용 하려면 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> VSEDITPROPID_ViewLangOpt_WordWrap의 값을 지정 `vt` 에 대 한는 `idprop` 매개 변수입니다. 이 호출 `vt` VT_BOOL 형식의 변형 및 `vt.boolVal` 가 VARIANT_TRUE입니다.  
  
## <a name="resetting-changed-view-settings"></a>변경 된 보기 설정을 다시 설정  
 핵심 편집기 인스턴스에 대 한 설정 변경 된 보기를 다시 설정 하려면 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> 메서드의 적절 한 설정 값을 지정 하 고는 `idprop` 매개 변수입니다.  
  
 예를 들어, 자유롭게 float로 자동 줄 바꿈 있도록 있습니다 것에서 제거 속성 범주를 호출 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A> VSEDITPROPID_ViewLangOpt_WordWrap에 대 한 값을 지정 하 고는 `idprop` 매개 변수입니다.  
  
 제거할 핵심 편집기에 대 한 변경 된 모든 설정을 한 번에 VSEDITPROPID_ViewComposite_AllCodeWindowDefaults, vt에 대 한 값을 지정 합니다 `idprop` 매개 변수입니다. 이 호출에서 vt VT_BOOL 형식의 VARIANT 이며 vt.boolVal VARIANT_TRUE입니다.  
  
## <a name="see-also"></a>참고 항목  
 [핵심 편집기 내에서](../extensibility/inside-the-core-editor.md)   
 [레거시 API를 사용 하 여 텍스트 보기에 액세스](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [옵션 대화 상자](../ide/reference/options-dialog-box-visual-studio.md)
