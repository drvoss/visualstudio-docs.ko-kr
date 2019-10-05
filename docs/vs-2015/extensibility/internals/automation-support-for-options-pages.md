---
title: 옵션 페이지에 대 한 자동화 지원 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7cb2634f5a16c62222cf360065cae0c22aef6667
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157249"
---
# <a name="automation-support-for-options-pages"></a>옵션 페이지의 자동화 지원
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Vspackage는 사용자 지정을 제공할 수 있습니다 **옵션** 대화 상자에 **도구** 메뉴 (도구 옵션 페이지)에서 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 및 자동화 모델에 제공할 수 있습니다.  
  
## <a name="tools-options-pages"></a>도구 옵션 페이지  
 만들려면를 **도구 옵션** 페이지에서 VSPackage에 VSPackage의 구현을 통해 환경에 반환 하는 사용자 컨트롤 구현을 제공 해야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 메서드를 (또는 관리 코드에 대 한는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 메서드)입니다.  
  
 이 선택 사항 이지만 자동화 모델을 통해이 새 페이지에 대 한 액세스를 허용 하도록 좋습니다. 다음 단계를 통해이 수행할 수 있습니다.  
  
1. 확장 된 <xref:EnvDTE._DTE.Properties%2A> IDispatch에서 파생 된 개체의 구현을 통해 개체입니다.  
  
2. 구현을 반환 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 메서드 (또는 관리 코드에 대 한는 <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> 메서드) IDispatch에서 파생 된 개체입니다.  
  
3. Automation 소비자를 호출 하는 경우는 <xref:EnvDTE._DTE.Properties%2A> 사용자 지정 메서드 **옵션** 속성 페이지에서이 환경에서는 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 가져올 사용자 지정 하는 방법 **도구 옵션** 페이지의 자동화 구현입니다.  
  
4. VSPackage의 자동화 개체는 다음 각를 제공 하는 데 사용 됩니다 <xref:EnvDTE.Property> 반환한 <xref:EnvDTE._DTE.Properties%2A>합니다.  
  
   사용자 지정 도구 옵션 페이지를 구현 하는 샘플을 보려면 [VSSDK 샘플](../../misc/vssdk-samples.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [프로젝트 개체 노출](../../extensibility/internals/exposing-project-objects.md)
