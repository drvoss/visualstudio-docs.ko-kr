---
title: VSTextView 개체 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22e4d4cdf1e5ca610dbdb067f8195fb730139c3d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690694"
---
# <a name="vstextview-object"></a>VSTextView 개체
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

텍스트 보기에는 사용자를 보고 텍스트 버퍼의 유니코드 텍스트를 편집할 수 있는 창입니다. 기본적으로 뷰는 편집기로 대부분의 사용자가 어떤 가리킵니다. 뷰는 버퍼에서 다양 한 텍스트 계층 (줄 바꿈, 개요 텍스트 및 등)로 구분 됩니다, 때문에 뷰 버퍼에 있는 텍스트의 정확한 표시 되도록 보장 되지 않습니다. 텍스트 보기에 대 한 자세한 내용은 참조 하세요. [레거시 API를 사용 하 여 텍스트 보기에 액세스](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 다음 표에서 인터페이스를 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> 개체입니다.  
  
|인터페이스|설명|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|표준 OLE 인터페이스입니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|표준 OLE 인터페이스입니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|표준 OLE 인터페이스입니다.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|표준 OLE 인터페이스입니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|복합 작업 (즉, 실행 취소/다시 실행의 단일 단위로 그룹화 된 작업)를 만들을 수 있습니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|관리 및 보기를 액세스 하기 위한 기본 메서드를 제공 합니다. `IVsTextView` 하지 스레드로부터 안전 합니다.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|만들고는 창을 관리 합니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|텍스트 계층 상호 작용합니다.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|다른 스레드에서 작업을 수행합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [그림 편집](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer 개체](../extensibility/vstextbuffer-object.md)   
 [레거시 API를 사용하여 텍스트 보기에 액세스](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
