---
title: 속성 창 단추 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b66015ef2e2ab0c8105b6f84486fa890adbf8b1f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438391"
---
# <a name="properties-window-buttons"></a>속성 창 단추
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

개발 언어 및 제품 종류에 따라 특정 단추에 대 한 도구 모음에서 기본적으로 표시 되는 **속성** 창입니다. 모든 경우에는 **항목별**, **Alphabetized**합니다 **속성**, 및 **속성 페이지** 단추가 표시 됩니다. Visual C# 및 Visual Basic의 경우에 **이벤트** 단추가 표시 됩니다. 특정 시각적 개체의 C++ 프로젝트를 **VC + + 메시지** 하며 **VC 재정의** 단추가 표시 됩니다. 기타 프로젝트 형식에 대 한 추가 단추를 표시 될 수 있습니다. 단추에 대 한 자세한 내용은 합니다 **속성** 창 참조 [속성 창](../../ide/reference/properties-window.md)합니다.  
  
## <a name="implementation-of-properties-window-buttons"></a>속성 창 단추 구현  
 클릭할 때 합니다 **항목별** 단추를 Visual Studio 호출은 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 범주별로 정렬 하려면 해당 속성 포커스가 있는 개체의 인터페이스입니다. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 구현 되는 `IDispatch` 에 표시 되는 개체를 **속성** 창입니다.  
  
 11 음수 값이 들어 있는 미리 정의 된 속성 범주에 있습니다. 사용자 지정 범주를 정의할 수 있지만 할당 하는 해당 양수 값 미리 정의 된 범주와 구별 하는 것이 좋습니다.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> 메서드는 지정된 된 속성에 대 한 적절 한 속성 범주 값을 반환 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> 메서드 범주 이름을 포함 하는 문자열을 반환 합니다. Visual Studio 표준 속성 범주 값을 알고 있기 때문에 사용자 지정 범주 값에 대 한 지원을 제공 해야 합니다.  
  
 클릭할 때 합니다 **Alphabetized** 단추 속성 이름별 사전순으로 표시 됩니다. 이름으로 검색 되 `IDispatch` 지역화 정렬 알고리즘에 따라 합니다.  
  
 경우는 **속성** 창이 열려 합니다 **속성** 단추는 자동으로 표시 선택 된 상태로. 환경의 다른 파트에는 동일한 단추 표시 되 고 표시 하려면 클릭 합니다 **속성** 창입니다.  
  
 합니다 **속성 페이지** 단추를 사용할 수 없는 경우 `ISpecifyPropertyPages` 선택한 개체에 대해 구현 되지 않았습니다. 속성 페이지는 일반적으로 솔루션 및 프로젝트와 연결 된 구성에 종속 된 속성을 표시 하지만 수도 연결 될 수 있으므로 프로젝트 항목을 사용 하 여 (예를 들어, 시각적 개체의에서 C++).  
  
> [!NOTE]
> 도구 모음 단추를 추가할 수 없습니다는 **속성** 비관리 코드를 사용 하 여 창입니다. 관리 되는 개체에서 파생 되는 도구 모음 단추를 추가 하려면 만들어야 <xref:System.Windows.Forms.Design.PropertyTab>합니다.  
  
## <a name="see-also"></a>참고 항목  
 [속성 확장](../../extensibility/internals/extending-properties.md)
