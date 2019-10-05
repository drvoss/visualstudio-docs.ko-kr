---
title: 사용자 지정 편집기의 구문 색 지정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - syntax coloring
ms.assetid: 74900b9a-baef-432a-8231-4568fb5e19ad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff717c8586e22d82a79344dd3c134c604f868d10
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316645"
---
# <a name="syntax-coloring-in-custom-editors"></a>사용자 지정 편집기의 구문 색 지정
핵심 편집기를 포함 하 여 visual Studio 환경 SDK 편집기를 특정 구문 항목을 식별 하 여 지정 된 문서 보기에 대 한 지정 된 색을 사용 하 여 표시할 언어 서비스를 사용 합니다.

## <a name="colorization-requirements"></a>색 지정 요구 사항
 언어 서비스의 colorizer를 구현 하는 모든 편집기는 다음 작업을 수행 해야 합니다.

1. 구현 하는 개체를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 텍스트 색으로 표시를 하 고 구현 하는 개체를 관리 하려면 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 텍스트의 문서 뷰를 제공 합니다.

2. 언어 서비스의 식별 GUID를 사용 하 여 VSPackage의 서비스 공급자를 쿼리하여 특정 언어 서비스에 대 한 인터페이스를 가져옵니다.

3. 호출 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.SetLanguageServiceID%2A> 구현 하는 개체 메서드의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>합니다. 이 메서드를 사용 하 여 언어 서비스 연결을 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 텍스트 색으로 표시를 관리 하는 VSPackage 구현 합니다.

## <a name="core-editor-usage-of-a-language-services-colorizer"></a>언어 서비스의 Colorizer 핵심 편집기 사용
 핵심 편집기, 구문 분석 및 언어 서비스의 colorizer 별로 텍스트의 렌더링의 인스턴스에서 colorizer 사용 하 여 언어 서비스를 가져온 경우는 사용자의 추가 개입 없이 자동으로 발생 합니다.

 IDE 투명 하 게 합니다.

- 구문 분석 하 고 추가 되거나의 구현에서 수정 될 텍스트 분석 colorizer 필요에 따라 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>합니다.

- 제공 하는 문서 보기에서 제공 하는 표시 되도록는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 구현이 업데이트 되어를 colorizer 반환한 정보를 사용 하 여 다시 표시 합니다.

## <a name="non-core-editor-usage-of-a-language-services-colorizer"></a>언어 서비스의 Colorizer 비핵심 편집기 사용
 비-핵심 편집기 인스턴스 언어 서비스의 구문 색 지정 서비스를 사용할 수도 있지만 명시적으로 검색 및 서비스의 colorizer를 적용 하 고 되어야 직접 자신의 문서 보기를 다시 그려야 합니다.

 이 작업을 수행 하려면 비핵심 편집기를 해야 합니다.

1. 언어 서비스의 colorizer 개체를 가져올 (구현 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer2>). VSPackage이 작업을 호출 하 여 수행 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> 언어 서비스의 인터페이스에서 메서드.

2. 호출 된 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 텍스트의 특정 범위를 색이 지정 된 수를 요청 하는 방법입니다.

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 색으로 표시할 텍스트의 각 문자에 대 한 범위, 값의 배열을 반환 합니다. 또한 색 항목, 설명, 키워드 또는 데이터 형식 등의 특정 형식으로 텍스트 범위를 식별합니다.

3. 반환 된 색 지정 정보를 사용 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> repaint를 해당 텍스트를 표시 합니다.

> [!NOTE]
> Colorizer 언어 서비스를 사용 하는 것 외에도 VSPackage는 범용 Visual Studio 환경 SDK 텍스트 색 지정 메커니즘을 사용 하도록 선택할 수 있습니다. 이 메커니즘에 대 한 자세한 내용은 참조 하세요. [를 사용 하 여 글꼴 및 색](../extensibility/using-fonts-and-colors.md)합니다.

## <a name="see-also"></a>참고 항목

- [레거시 언어 서비스의 구문 색 지정](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [구문 색 지정 구현](../extensibility/internals/implementing-syntax-coloring.md)
- [방법: 기본 제공 색 항목 사용](../extensibility/internals/how-to-use-built-in-colorable-items.md)
- [사용자 지정 색 항목](../extensibility/internals/custom-colorable-items.md)