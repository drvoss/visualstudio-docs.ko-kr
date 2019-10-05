---
title: 속성 Window Fields and Interfaces | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700817"
---
# <a name="properties-window-fields-and-interfaces"></a>Properties Window Fields and Interfaces
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

모델에 표시 되는 정보를 확인 하려면 선택 합니다 **속성** IDE에서 포커스가 있는 창에서 창 기반 합니다. 모든 창 및 선택된 된 창 내에서 개체에 전역 선택 컨텍스트에 푸시된 해당 선택 컨텍스트 개체를 가질 수 있습니다. 해당 창에 포커스가 있는 경우 창 프레임의 값을 사용 하 여 전역 선택 컨텍스트를 업데이트 하는 환경입니다. 포커스 변경 되 면 선택 항목 컨텍스트를 그렇습니다.  
  
## <a name="tracking-selection-in-the-ide"></a>IDE에서 추적 선택  
 창 프레임 또는 IDE를 소유한 사이트에 라는 서비스 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>합니다. 다음 단계에서는 다른 열린 창으로 포커스를 변경 하거나에서 다른 프로젝트 항목을 선택 하는 사용자가 발생 한 항목을 변경 하는 방법 설명 **솔루션 탐색기**를 에서표시되는내용을변경하기위해구현됩니다 **속성** 창입니다.  
  
1. 선택한 창 호출에 배치 되는 VSPackage로 생성 된 개체 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> 필요가 <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>합니다.  
  
2. 선택한 기간에 제공한 선택 컨테이너 자체 만듭니다 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 개체입니다. VSPackage 호출 하는 선택 항목이 변경 하면 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 환경에서 모든 수신기에 알리기 위해 포함 하는 **속성** 변경의 창. 또한 계층 구조 및 항목 관련 정보를 새 선택 영역에 대 한 액세스를 제공 합니다.  
  
3. 호출 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 선택한 계층 항목에 전달 하는 `VSHPROPID_BrowseObject` 매개 변수를 채웁니다는 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 개체입니다.  
  
4. 파생 된 개체를 [IDispatch 인터페이스](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) 에 대해 반환 됩니다 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 항목을 요청 하 고 환경에 래핑되어는 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (다음 단계 참조). 환경에 대 한 두 번째 호출에서는 호출에 실패 하는 경우 `IVsHierarchy::GetProperty`, 선택 컨테이너 전달 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> 항목 계층 구조를 제공 합니다.  
  
    VSPackage를 만들지 않습니다 프로젝트가 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 구현 하는 VSPackage의 환경에서 제공한 창 (예를 들어 **솔루션 탐색기**) 생성 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 을 대신 합니다.  
  
5. 메서드를 호출 하는 환경 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 기준으로 개체를 가져오는 데는 `IDispatch` 인터페이스를 작성 하는 **속성** 창.  
  
   값을 **속성** 창이 변경 될, Vspackage 구현 `IVsTrackSelectionEx::OnElementValueChangeEx` 및 `IVsTrackSelectionEx::OnSelectionChangeEx` 요소 값에 변경 내용을 보고할 합니다. 환경을 다음 호출 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> 또는 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 표시 되는 정보를 유지 하는 **속성** 창이 속성 값과 동기화 합니다. 자세한 내용은 [속성 창에서 속성 값 업데이트](../../misc/updating-property-values-in-the-properties-window.md)합니다.  
  
   다른 선택 하는 것 외에도 프로젝트 항목 **솔루션 탐색기** 해당 항목과 관련 된 속성을 표시 하려면 선택할 수도 있습니다에서 사용할 수 있는 드롭다운 목록을 사용 하 여 폼 이나 문서 창 내에서 다른 개체는 **속성** 창입니다. 자세한 내용은 [속성 창 개요 목록](../../extensibility/internals/properties-window-object-list.md)합니다.  
  
   정보에 표시 되는 방식을 변경할 수 있습니다 합니다 **속성** 범주를 알파벳에서 창 그리드의 는에서해당단추를클릭하여선택한개체에대한속성페이지를도열수,사용가능한경우 **속성** 창입니다. 자세한 내용은 [속성 창 단추](../../extensibility/internals/properties-window-buttons.md) 하 고 [속성 페이지](../../extensibility/internals/property-pages.md)합니다.  
  
   맨 마지막으로 **속성** 창에서 선택한 필드에 대 한 설명을 포함 합니다 **속성** 창 그리드입니다. 자세한 내용은 [속성 창에서 필드 설명 가져오기](../../misc/getting-field-descriptions-from-the-properties-window.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [속성 확장](../../extensibility/internals/extending-properties.md)
