---
title: 구문 색 지정 구현 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax coloring, implementing
- editors [Visual Studio SDK], colorizing text
- text, colorizing in editors
ms.assetid: 96e762ca-efd0-41e7-8958-fda4897c8c7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3f577f4cf21110a1b40680059b385d413c9c6902
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324230"
---
# <a name="implementing-syntax-coloring"></a>구문 색 지정 구현
구문 색 지정을 제공 하는 언어 서비스 파서를 색 항목 배열로 텍스트 줄을 변환한 이러한 색 항목에 해당 하는 토큰 형식을 반환 합니다. 파서가 색 항목 목록에 속해 있는 토큰 유형을 반환 해야 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 적절 한 토큰 형식 colorizer 개체에 의해 할당 된 특성에 따라 코드 창에서 각 색 항목을 표시 합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 파서 인터페이스를 지정 하지 않는 파서가 구현은 전적으로 사용자 및 합니다. 그러나 Visual Studio 언어 패키지 프로젝트의 기본 파서 구현이 제공 됩니다. 관리 코드에 대해 관리 패키지 프레임 워크 (MPF) 텍스트 색을 지정 하는 것에 대 한 전체 지원의 제공 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 구문 색 지정을 구현 하는 새로운 방법에 대 한 자세한 참조 [연습: 텍스트를 강조 표시](../../extensibility/walkthrough-highlighting-text.md)합니다.

> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="steps-followed-by-an-editor-to-colorize-text"></a>텍스트 색을 지정 하는 편집기에서 다음 단계

1. 편집기를 호출 하 여는 colorizer 가져옵니다 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 메서드는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 개체.

2. 편집기를 호출 하 여는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStateMaintenanceFlag%2A> 는 colorizer 각 줄은 colorizer 외부 유지 관리의 상태를 해야 하는지 여부를 결정 하는 방법입니다.

3. 편집기를 호출 합니다 colorizer는 colorizer 외부 유지 관리 상태에 필요한 경우는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.GetStartState%2A> 메서드 첫 번째 줄의 상태를 가져옵니다.

4. 편집기 버퍼의 각 줄에 대 한 호출을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 다음 단계를 수행 하는 메서드:

    1. 텍스트 줄의 텍스트를 토큰으로 변환할 스캐너에 전달 됩니다. 각 토큰에 토큰 텍스트와 토큰 형식을 지정합니다.

    2. 토큰 유형이 인덱스 색 항목 목록으로 변환 됩니다.

    3. 토큰 정보를 줄의 문자에 해당 하는 배열의 각 요소는 배열 입력에 사용 됩니다. 배열에 저장 된 값은 색 항목 목록 인덱싱합니다.

    4. 줄의 끝에서 상태는 각 줄에 대해 반환 됩니다.

5. colorizer 상태를 유지에 필요한 경우 편집기는 해당 줄에 대 한 상태를 캐시 합니다.

6. 편집기에서 반환 된 정보를 사용 하 여 텍스트의 줄 렌더링은 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 메서드. 이 경우 다음 단계를 수행해야 합니다.

    1. 줄에 각 문자에 대해 색 항목 인덱스를 가져옵니다.

    2. 기본 색 항목을 사용 하는 경우 편집기의 색 항목 목록에 액세스 합니다.

    3. 그렇지 않으면 언어 서비스의 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 색 항목을 가져오는 방법입니다.

    4. 화면에 텍스트를 렌더링 하 색 항목의 정보를 사용 합니다.

## <a name="managed-package-framework-colorizer"></a>관리 되는 패키지 프레임 워크 Colorizer
 (MPF)에서 관리 되는 패키지 프레임 워크는 colorizer를 구현 하는 데 필요한 모든 클래스를 제공 합니다. 언어 서비스 클래스에서 상속 해야 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스 및 필요한 메서드를 구현 합니다. 구현 하 여 스캐너 및 파서를 제공 해야 합니다는 <xref:Microsoft.VisualStudio.Package.IScanner> 인터페이스 및에서 해당 인터페이스의 인스턴스를 반환 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 메서드 (에서 구현 해야 하는 방법 중 하나는 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스). 자세한 내용은 [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)합니다.

## <a name="see-also"></a>참고 항목
- [방법: 기본 제공 색 항목 사용](../../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [사용자 지정 색 항목](../../extensibility/internals/custom-colorable-items.md)
- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)