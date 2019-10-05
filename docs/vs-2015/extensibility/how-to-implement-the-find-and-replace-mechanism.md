---
title: '방법: 구현 찾기 및 바꾸기 메커니즘 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - find and replace
ms.assetid: bbd348db-3d19-42eb-99a2-3e808528c0ca
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4362d0b0c3f013ce6f38d13265dcc181c77012c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62548698"
---
# <a name="how-to-implement-the-find-and-replace-mechanism"></a>방법: 구현 찾기 및 바꾸기 메커니즘
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 찾기/바꾸기를 구현 하는 두 가지를 제공 합니다. 한 가지 방법은 셸에 텍스트 이미지를 전달 하 고 검색, 강조 표시 및 대체 텍스트를 처리 하도록 하는 것입니다. 이 여러 텍스트 범위를 지정할 수가 있습니다. 또는 VSPackage는 자체에서 이러한 기능을 제어할 수 있습니다. 두 경우 모두 현재 대상 및 열려 있는 모든 문서에 대 한 대상에 대 한 shell에 알려야 합니다.  
  
### <a name="to-implement-findreplace"></a>찾기/바꾸기 구현 하려면  
  
1. 구현 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> 프레임 속성에서 반환한 개체 중 하나에서 인터페이스 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>합니다. 사용자 지정 편집기를 만드는 경우 사용자 지정 편집기 클래스의 일부로이 인터페이스를 구현 해야 합니다.  
  
2. 사용 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetCapabilities%2A> 메서드 편집기를 지 원하는 옵션을 지정 하 고 텍스트 이미지 검색를 구현 하는지 여부를 나타냅니다.  
  
     편집기 텍스트 이미지 검색을 지 원하는 경우 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>합니다.  
  
     그렇지 않으면 구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> 고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>입니다.  
  
3. 구현 하는 경우는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A> 하 고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A> 메서드를 호출 하 여 검색 작업을 간소화할 수 있습니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper> 인터페이스입니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindHelper>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.GetSearchImage%2A>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROPID>
