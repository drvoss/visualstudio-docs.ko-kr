---
title: 속성 창 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fd4be229338d1a09c22b4d81384dc90f0544fa39
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700750"
---
# <a name="properties-window-overview"></a>속성 창 개요
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

합니다 **속성** 창을 사용 하 여 windows에서 사용할 수 있는 두 가지 주요 유형에서 선택한 개체에 대 한 속성을 표시 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 통합된 개발 환경 (IDE)입니다. 이러한 두 창의 유형은 다음과 같습니다.  
  
- 솔루션 탐색기, 클래스 뷰 및 개체 브라우저와 같은 도구 창  
  
- 이러한 편집기 및 디자이너와 forms 디자이너, XML 편집기, HTML 편집기를 포함 하는 문서 창  
  
## <a name="using-the-properties-window"></a>속성 창 사용  
 합니다 **속성** 단일 또는 여러 선택된 항목의 속성 창에 표시 됩니다. 여러 항목을 선택 하는 경우 선택한 모든 개체에 대 한 모든 속성의 교집합 표시 됩니다.  
  
 폼 디자인 창 또는 COM + 메타 데이터를 사용 하 여 HTML 편집기 내에서 선택한 개체와 관련 된 이벤트에 표시 되는 **속성** 창입니다. 예를 들어, 단추를 선택 하 수와 같은 연관 된 이벤트를 표시는 `OnClick` 해당 단추에 연결할 수 있는 이벤트입니다.  
  
 이벤트에 표시 된 **속성** 창 코드에 바인딩되는 개체를 사용 하 여 주로 사용 됩니다. 코드와 관련이 없는 파일 형식 편집 하는 경우 모든 이벤트가 포함 하지 않을 수 있습니다. 이벤트에만 표시 됩니다는 **속성** 있으면 다음 코드를 실행 하는 특정 개체와 관련 된 특정 이벤트 간에 바인딩을 창입니다. 이 예제는 해당 개체가 활성화 될 때 실행 되는 선택한 개체 코드가 것입니다.  
  
 다음 표에서 사용 하는 기본 인터페이스를 나열 합니다 **속성** 창입니다.  
  
|인터페이스 이름|설명|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|범주 목록을 제공 합니다 **속성** 창 범주에 각 속성에 매핑합니다.|  
|[IDispatch 인터페이스](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|개체의 메서드 및 속성 프로그래밍 도구 및 자동화를 지 원하는 다른 응용 프로그램을 노출 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|호출 하는 줄임표 (...) 단추를 제공 *작성기* 개체 자체에 의해 구현 하는 모달 대화 상자 창을 열입니다. 값을 텍스트 필드에 사용자가 쉽게 형식화 되지 않은 경우 사용 합니다. 예를 들어 열려면 RGB 값을 결정 하는 색 선택은이 서비스를 사용할 수 있습니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|에 표시 된 정보를 업데이트 하는 데 사용 되는 개체에 대 한 액세스를 제공 합니다 **속성** 창입니다. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 표시할 관련된 속성을 사용 하 여 선택할 수 있는 개체를 포함 하는 각 창에 대 한 Vspackage에 의해 구현 됩니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|인터페이스 및 구조체의 필드의 메서드와 같은 개체의 형식에 대 한 정보를 제공합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Vspackage를 선택 이벤트의 알림을 받을 수 및 현재 프로젝트 계층 구조, 항목, 요소 값 및 명령 UI 컨텍스트 정보를 검색할 수 있습니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|여러 선택 항목에 액세스할 수 있는 환경을 제공합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|표시 되는 일부 속성의 지역화 된 이름을 제공 하는 데 사용 합니다 **속성** 창입니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|현재 선택 영역, 요소 값 또는 명령 UI 컨텍스트를 변경의 등록 된 Vspackage를에 알립니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|현재 선택 영역 변경의 환경을 알리고 계층 및 항목 관련 정보를 새 선택 영역에 대 한 액세스를 제공 합니다.|  
  
 대 한 자세한 내용은 `IDispatch`, MSDN library를 참조 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [확장 속성](../../extensibility/internals/extending-properties.md)   
 [속성 창 필드 및 인터페이스](../../extensibility/internals/properties-window-fields-and-interfaces.md)
