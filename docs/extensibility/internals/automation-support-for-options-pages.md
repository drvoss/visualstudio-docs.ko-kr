---
title: 옵션 페이지에 대 한 자동화 지원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Tools Options pages [Visual Studio SDK], automation support
- automation [Visual Studio SDK], creating Tools Options pages
ms.assetid: 0b25b82c-7432-4e0a-9e84-350269ba8260
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0bf997205979cdfbb9c9f03492a5943f458e2d9c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66342269"
---
# <a name="automation-support-for-options-pages"></a>Automation 옵션 페이지에 대 한 지원
Vspackage는 사용자 지정을 제공할 수 있습니다 **옵션** 대화 상자에 **도구** 메뉴 (**도구 옵션** 페이지)에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 자동화 가능 하도록 만들 수 및 모델입니다.

## <a name="tools-options-pages"></a>도구 옵션 페이지
 만들려는 **도구 옵션** 페이지에서 VSPackage에 VSPackage의 구현을 통해 환경에 반환 하는 사용자 컨트롤 구현을 제공 해야 합니다는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 메서드. (또는 관리 코드는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 메서드.)

 이 선택 사항 이지만 자동화 모델을 통해이 새 페이지에 대 한 액세스를 허용 하도록 좋습니다. 다음 단계를 사용 하 여 수행할 수 있습니다.

1. 확장 된 <xref:EnvDTE._DTE.Properties%2A> IDispatch에서 파생 된 개체의 구현을 통해 개체입니다.

2. 구현을 반환 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 메서드 (또는 관리 코드에 대 한는 <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> 메서드) IDispatch에서 파생 된 개체입니다.

3. Automation 소비자를 호출 하는 경우는 <xref:EnvDTE._DTE.Properties%2A> 사용자 지정 메서드 **옵션** 속성 페이지에서이 환경에서는 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 가져올 사용자 지정 하는 방법 **도구 옵션** 페이지의 자동화 구현입니다.

4. VSPackage의 자동화 개체는 다음 각를 제공 하는 데 사용 됩니다 <xref:EnvDTE.Property> 반환한 <xref:EnvDTE._DTE.Properties%2A>합니다.

   사용자 지정 구현 샘플 **도구 옵션** 페이지를 참조 하십시오 [VSSDK 샘플](https://aka.ms/vs2015sdksamples)합니다.

## <a name="see-also"></a>참고자료
- [프로젝트 개체 노출](../../extensibility/internals/exposing-project-objects.md)