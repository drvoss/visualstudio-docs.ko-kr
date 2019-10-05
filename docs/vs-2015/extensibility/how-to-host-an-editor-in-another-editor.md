---
title: '방법: 다른 편집기에서 편집기 호스트 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204175"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>방법: 다른 편집기에서 편집기 호스트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio에서 다른 자가 호스팅 창의 부모 창으로 지정 하 여 호스팅할 수 있습니다. 이렇게 하려면 매개 변수를 설정할 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 및 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 자식 창 프레임에 있습니다.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>편집기를 호스트 하는 창 프레임을 설정 하려면  
  
1. 자식 창을 만들어 호스팅된 편집기로 편집기를 지정 합니다.  
  
     이 창은 편집기의 텍스트는 어디로 야 합니다.  
  
2. 사용 하 여 호스팅 편집기 만들기를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 또는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> 메서드.  
  
3. 설정 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 및 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> 이러한 속성을 매개 변수로 전달 하 여 호스팅된 편집기의 프레임 창 구현에서 속성을 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> 메서드를 각각.  
  
     이러한 매개 변수를 검색 해야 할 경우 이러한 속성을 전달 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> 메서드.  
  
4. 호출 된 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> 포함 된 편집기에 대 한 메서드.  
  
     편집기를 포함 하는 편집기의 호스트 된 창에 나타납니다.  
  
## <a name="robust-programming"></a>강력한 프로그래밍  
 합니다 **응용 프로그램 디자이너** Visual Studio Team Edition for Architects의 다른 편집기를 호스트 하는 편집기 창 프레임의 예입니다. 합니다 **응용 프로그램 디자이너** 다른 디자이너의 오른쪽 창에서 호스트 합니다. 디자이너 패널 (또는 **속성** 페이지)에 포함 된 디자이너의 각 포함 된 창 프레임에 추가 됩니다.
