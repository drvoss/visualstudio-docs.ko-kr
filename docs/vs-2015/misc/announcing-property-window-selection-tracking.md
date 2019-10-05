---
title: 속성 창 선택 영역 추적 발표 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], property pages support
- property pages, tracking selection
- Properties window, tracking selection
- selection, tracking
- editors [Visual Studio SDK], Properties window support
ms.assetid: a7536f82-afd7-4894-9a60-84307fb92b7e
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 6296993d3a1f5039024556f09b721daa82ca4f53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63002445"
---
# <a name="announcing-property-window-selection-tracking"></a>속성 창 선택 영역 추적 발표
사용 하려는 경우는 **속성** 창 또는 **속성** 페이지, 예를 들어, 폼, 텍스트 또는 구하려는 속성을 보려는 방법 잘 알고 있어야 합니다. 그런 다음 선택 하면 선택 영역을 조정 합니다. 예를 들어 단일 선택 또는 여러 선택 영역에 있는지 알아야 합니다. 그런 다음 해당 선택 영역 형식 (단일 또는 여러) 사용 하 여 IDE에 발표 해야는 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> 인터페이스입니다. 이 인터페이스에 필요한 정보를 제공 합니다 **속성** 창입니다.  
  
### <a name="to-announce-selection-to-the-environment"></a>이를 알리도록 환경 선택  
  
1. 호출 `QueryInterface` 에 대 한 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>합니다.  
  
    1. 이 작업을 수행 하려면 만들 때 보기에 전달 되는 사이트 포인터를 사용 합니다.  
  
    2. 호출 `QueryService` 에 대 한 뷰에서 `SID_STrackSelection` 서비스입니다.  
  
         에 대 한 포인터를 반환 하는이 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>합니다.  
  
2. 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 선택이 변경 될 때마다 메서드 및 구현 하는 개체에 대 한 포인터를 전달 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>합니다.  
  
     선택 컨테이너 개체에서 단일 또는 다중 선택을 사용할 수 있습니다에 선택 정보를 포함 하는 `IDispatch` 개체입니다. 호출을 <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> 메서드를 알립니다 합니다 **속성** 선택 영역이 변경 하는 창. 합니다 **속성** 창에서 다음 개체를 사용 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 단일 또는 다중 선택을 발생 하는지 여부 및 실제 개체 선택 항목을 확인 하려면.  
  
     여러 항목을 지정 하는 경우 해당 **속성** 창 개체에 대 한 공용 속성의 교집합을 찾습니다. 단일 개체 선택 영역을 지정 하는 경우 해당 **속성** 의 모든 개체에 대 한 속성 창에 표시 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [확장 속성](../extensibility/internals/extending-properties.md)   
 [속성 페이지(Visual C++)](../extensibility/internals/property-pages.md)