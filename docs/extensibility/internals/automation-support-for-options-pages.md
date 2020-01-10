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
ms.openlocfilehash: 03360bfc01110e7b4ef73956f0199aaaed9cee2c
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75848964"
---
# <a name="automation-support-for-options-pages"></a>옵션 페이지에 대 한 자동화 지원
Vspackage는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 **도구** 메뉴 (**도구 옵션** 페이지)에 사용자 지정 **옵션** 대화 상자를 제공 하 고이를 자동화 모델에 사용할 수 있게 만들 수 있습니다.

## <a name="tools-options-pages"></a>도구 옵션 페이지
 **도구 옵션** 페이지를 만들려면 VSPackage는 VSPackage의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 메서드 구현을 통해 환경에 반환 되는 사용자 정의 컨트롤 구현을 제공 해야 합니다. 또는 관리 코드의 경우 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> 메서드입니다.)

 선택 사항 이지만 자동화 모델을 통해이 새 페이지에 대 한 액세스를 허용 하는 것이 좋습니다. 이렇게 하려면 다음 단계를 수행 합니다.

1. IDispatch 파생 개체의 구현을 통해 <xref:EnvDTE._DTE.Properties%2A> 개체를 확장 합니다.

2. IDispatch 파생 개체에 대 한 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 메서드 또는 관리 코드의 경우 <xref:Microsoft.VisualStudio.Shell.Package.GetAutomationObject%2A> 메서드의 구현을 반환 합니다.

3. 자동화 소비자가 사용자 지정 **옵션** 속성 페이지에서 <xref:EnvDTE._DTE.Properties%2A> 메서드를 호출 하는 경우 환경에서는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 메서드를 사용 하 여 사용자 지정 **도구 옵션** 페이지의 자동화 구현을 가져옵니다.

4. 그런 다음 VSPackage의 자동화 개체를 사용 하 여 <xref:EnvDTE._DTE.Properties%2A>에서 반환 하는 각 <xref:EnvDTE.Property>를 제공 합니다.

   사용자 지정 **도구 옵션** 페이지를 구현 하는 샘플을 보려면 고가 나 [진한 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples)을 참조 하세요.

## <a name="see-also"></a>참조
- [프로젝트 개체 노출](../../extensibility/internals/exposing-project-objects.md)
