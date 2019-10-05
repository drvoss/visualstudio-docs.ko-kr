---
title: 속성 표를 표시 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5fd5e17d764336cda450c726023b209f89f194a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68180389"
---
# <a name="properties-display-grid"></a>속성 표시 그리드
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

합니다 **속성** 표 내의 필드 창에 표시 됩니다. 왼쪽된 열에 속성 이름이; 있습니다. 오른쪽 열에 속성 값을 포함합니다.  
  
## <a name="working-with-the-grid"></a>그리드와 작동합니다.  
 두 개의 열은 디자인 타임과 현재 설정을 변경할 수 있는 구성에 관계 없이 속성을 보여 줍니다. 모든 속성을 표시 될 수 있습니다 하는 참고 합니다. 속성을 설정할 수 있습니다 구현 하 여 예를 들어 숨기는지를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> 메서드. 참조, 자식 속성을 가진 속성 숨기기에 특히 [숨기기 속성을가 자식 속성](../../misc/hiding-properties-that-have-child-properties.md)합니다.  
  
 에 정보를 **속성** 창, IDE 사용 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>합니다. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 각 창에 표시할 관련된 속성을 사용 하 여 선택할 수 있는 개체를 포함 하는 Vspackage에 의해 호출 되는 **속성** 창입니다. **솔루션 탐색기**의 구현을 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 호출 `GetProperty` 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 계층 구조에서 지정 되며 검색이 가능 개체를 획득 하 여 프로젝트 계층 구조에서.  
  
 VSPackage를 지원 하지 않는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, IDE를 사용 하려고 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 에 대 한 값을 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 항목 계층 구조를 제공 합니다.  
  
 VSPackage를 만들 필요가 없습니다 프로젝트가 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 구현 하는 창을 IDE에서 제공한 패키지 (예를 들어 **솔루션 탐색기**) 생성 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 을 대신 합니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> IDE에 의해 호출 되는 세 가지 방법으로 구성 됩니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> 에 표시할 선택한 개체 수가 포함 된 **속성** 창입니다.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 반환 된 `IDispatch` 에 표시 하기 위해 선택한 개체를 **속성** 창.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> 반환한 개체에 대 한 수 있도록 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 사용자가 선택할 수 있습니다. 그러면 VSPackage에 시각적으로 UI에서 사용자에 게 표시 되는 선택을 업데이트 합니다.  
  
  합니다 **속성** 창에서 정보를 추출 합니다 `IDispatch` 탐색 속성을 검색 하는 개체입니다. 속성 브라우저를 사용 하 여 `IDispatch` 쿼리하여 지원 개체를 요청할 속성 `ITypeInfo`에서 얻을 수 있는 `IDispatch::GetTypeInfo`합니다. 그러면 브라우저가 채우는 데 이러한 값을 사용 합니다 **속성** 창과 표에 표시 된 개별 속성에 대 한 값을 변경 합니다. 속성 정보는 개체 자체 내에서 유지 됩니다.  
  
  반환된 된 개체를 지원 하므로 `IDispatch`를 호출자에 게 호출 하 여 개체의 이름과 같은 정보를 가져올 수 있습니다 `IDispatch::Invoke` 또는 `ITypeInfo::Invoke` 원하는 정보를 나타내는 미리 정의 된 디스패치 식별자 (DISPID)를 사용 하 여 합니다. 선언 된 Dispid이 사용자 정의 식별자와 충돌 하지 않도록 하려면 음수입니다.  
  
  합니다 **속성** 다양 한 형식의 필드는 선택한 개체의 특정 속성의 특성에 따라 창에 표시 됩니다. 이러한 필드는 편집 상자, 드롭 다운 목록 및 사용자 지정 편집기 대화 상자에 대 한 링크를 포함 합니다.  
  
- 열거 된 목록에 포함 된 값을 검색 한 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 쿼리를 `IDispatch`. 필드 이름을 두 번 클릭 하거나 값을 클릭 하 고 드롭다운 목록에서 새 값을 선택 하 여 열거 된 목록에서 가져온 값을 속성 표에서 변경할 수 있습니다. 열거 된 목록에서 설정을 미리 정의 된 속성을 사용 가능한 선택 항목 순환 속성 목록에서 속성 이름을 두 번 클릭 합니다. True/false와 같은 두 가지 선택 항목을 사용 하 여 미리 정의 된 속성에 대 한 선택 항목 간에 전환 하려면 속성 이름을 두 번 클릭 합니다.  
  
- 하는 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> 는 `false`의 값이 변경 되었음을 나타내는 값은 굵게에서 표시 됩니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> 값을 원래 값으로 다시 설정할 경우를 결정 하는 데 사용 됩니다. 따라서 변경할 수 있는 경우 기본값으로 다시 값을 마우스 오른쪽 단추로 클릭 하 고 선택 하 여 **재설정** 표시 합니다. 그렇지 않은 경우 기본값으로 다시 값을 수동으로 변경 해야 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 지역화 하 고 디자인 타임에 표시 되는 속성의 이름을 숨길 수 있지만 런타임에 표시 되는 속성 이름을 영향을 주지 않습니다.  
  
- 줄임표 (...) 단추를 클릭 하면 속성 값 (예: 색상 또는 글꼴 목록) 선택할 수 있는 사용자의 목록을 표시 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> 이러한 값을 제공 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [속성 확장](../../extensibility/internals/extending-properties.md)
