---
title: 레거시 API를 사용 하 여 텍스트 계층에 액세스 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text layers
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 975e8624a6ffbfe0c5ae7544f2b978487465e34e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148019"
---
# <a name="accessing-text-layers-by-using-the-legacy-api"></a>레거시 API를 사용하여 텍스트 레이어에 액세스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

일반적으로 텍스트 레이어에 텍스트 레이아웃의 일부 측면을 캡슐화합니다. 예를 들어, "함수에서-한 번" 계층 캐럿 (텍스트 삽입 지점)이 포함 된 함수 앞뒤 텍스트를 숨깁니다.  
  
 텍스트 레이어에 버퍼와 뷰 간에 있고 뷰는 버퍼의 내용을 표시 하는 방법을 수정 합니다.  
  
## <a name="text-layer-information"></a>텍스트 계층 정보  
 다음은 텍스트 계층에서 작동 하는 방법에 대해 설명 합니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]:  
  
- 구문 색 지정 및 표식을 사용 하 여 텍스트 레이어에 있는 텍스트를 표시할 수 있습니다.  
  
- 현재 고유한 계층을 구현할 수 없습니다.  
  
- 계층에 노출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>에서 파생 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>합니다. 텍스트 버퍼 자체 뷰를 기본 계층을 사용 하 여 다형적으로 처리할 수 있도록 하는 계층으로도 구현 됩니다.  
  
- 계층의 여러 보기와 버퍼 간에 식별할 수 있습니다. 아래 계층에만 각 계층은 처리 및 최상위 계층 뷰를 대부분 처리 합니다. (보기에는 버퍼에 대 한 정보.)  
  
- 계층은 하위 계층 에서만 발생할 수 있습니다. 표준 이벤트를 발생 하는 초과 위의 계층에는 영향을 줄 수 없습니다.  
  
- 편집기에서 숨겨진된 텍스트, 가상 텍스트 및 자동 줄 바꿈 계층으로 구현 됩니다. 직접 계층 상호 작용 하지 않고 가상 숨겨진된 텍스트를 구현할 수 있습니다. 자세한 내용은 [레거시 언어 서비스의 개요](../extensibility/internals/outlining-in-a-legacy-language-service.md) 고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>입니다.  
  
- 텍스트 레이어마다를 통해 노출 되는 자체 로컬 좌표계는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> 인터페이스입니다. 자동 줄 바꿈을 계층을 두 줄 포함할 수 있습니다 예를 들어, 기본 텍스트 버퍼를 한 줄만 포함 될 수 있습니다.  
  
- 계층을 통해 통신 하는 뷰는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> 인터페이스입니다. 이 인터페이스를 사용 하 여 버퍼 좌표를 사용 하 여 뷰 좌표를 조정 합니다.  
  
- 텍스트를 시작 하는 가상 텍스트 계층의 로컬 구현을 제공 해야 같은 모든 계층 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A>합니다.  
  
- 외에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, 텍스트 레이어를 구현 해야 합니다 <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> 에서 이벤트를 발생 시키는 및는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 [사용자 지정 편집기의 구문 색 지정](../extensibility/syntax-coloring-in-custom-editors.md)   
 [텍스트 마커를 사용 하 여 레거시 API를 사용 하 여](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [레거시 API를 사용하여 편집기 컨트롤 및 메뉴 사용자 지정](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)
