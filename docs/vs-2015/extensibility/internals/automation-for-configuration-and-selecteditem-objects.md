---
title: 구성 및 SelectedItem 개체 자동화 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157252"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>구성 SelectedItem 개체 자동화
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

빌드 및에서 선택한 항목 프로세스를 자동화할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]합니다.  
  
## <a name="automation-for-builds"></a>빌드에 대 한 자동화  
 빌드 또는 구성에 구현 하는 경우 제공 되는 자동화 모델이 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>합니다. 자세한 내용은 [빌드 구성 이해](../../ide/understanding-build-configurations.md)를 참조하세요.  
  
 VSPackage를 만들고 구성 옵션을 제어 하려는 경우 자동화 모델을 사용 해야 합니다.  
  
## <a name="automation-for-selecteditem"></a>SelectedItem에 대 한 자동화  
 에 대 한 구현을 제공 해야 합니다 `SelectedItem` Visual Studio 표준 구현을 포함 하기 때문에 개체입니다. 그러나 구현할 수 있습니다는 `SelectedItem` 것이 바람직 할 개체입니다. 포함 하는 개체를 구현 해야 합니다는 `SelectedItem` 인터페이스 및에 대 한 호출에 대 한 응답을 반환 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> VSITEMID 메서드로 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [자동화 모델에 영향을 주는](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [빌드 구성 이해](../../ide/understanding-build-configurations.md)
