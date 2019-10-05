---
title: 사용자 지정 색 항목 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- colorable items
- language services, custom colorable items
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd1d18a6fe142a3b405742dd9e74c1376e713687
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312907"
---
# <a name="custom-colorable-items"></a>사용자 지정 색 항목
언어 서비스의 일부로 사용자 지정 색 항목을 구현 하 여 형식 목록을 키워드 및 주석 등의 색을 지정 재정의할 수 있습니다.

## <a name="user-settings-of-colorable-items"></a>색 항목의 사용자 설정
 표시할 수 있습니다 합니다 **글꼴 및 색** 를 선택 하 여 대화 상자 **옵션** 에 **도구** 메뉴를 선택한 다음 **글꼴 및 색** 아래 **환경**합니다. 선택 하면 표시 되는 같은 **텍스트 편집기** 또는 **명령 창**의 **항목을 표시** 목록 상자를 표시 하는 모든 색 항목을 보여 줍니다. 볼 수 있으며, 글꼴, 크기, 전경색 및 각 색 항목에 대 한 배경색을 변경할 수 있습니다. 선택 사항을 레지스트리에서 캐시에 저장 되 고 색 항목 이름으로 액세스 합니다.

## <a name="presentation-of-colorable-items"></a>색 항목 표시
 IDE의 색 항목 사용자 재정의 처리 하기 때문에 합니다 **글꼴 및 색** 대화 상자에서 해야만 이름으로 각 사용자 지정 색 항목을 제공 합니다. 이 이름은에 나타나는 항목의 **항목을 표시** 목록. 색 항목 사전순으로 표시 합니다. 언어 서비스의 사용자 지정 색 항목 그룹을 시작할 수 있습니다 각 이름에 언어 이름의 예를 들어 **NewLanguage-주석** 하 고 **NewLanguage-키워드**합니다.

> [!CAUTION]
> 기존 색 항목 이름과 충돌 하지 않도록 하려면 색 항목 이름에 언어 이름을 포함 해야 합니다. 개발 중 색 항목 중 하나의 이름을 변경한 경우에 색 항목 액세스 된 처음 만들어진 캐시를 다시 설정 해야 합니다. 실험적 캐시를 다시 설정할 수 있습니다 합니다 **CreateExpInstance** 디렉터리에 일반적으로 Visual Studio SDK와 함께 설치 되는 도구:
>
> *C:\Program Files (x86)\Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin*
>
> 캐시를 재설정 하려면 입력 **CreateExpInstance /Reset**합니다. 에 대 한 자세한 내용은 **CreateExpInstance**를 참조 하십시오 [CreateExpInstance 유틸리티](../../extensibility/internals/createexpinstance-utility.md)합니다.

 색 항목 목록에서 첫 번째 항목 참조 되지 않습니다. 첫 번째 항목 인덱스에 해당 하는 색 항목 0 및 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 항상 기본 텍스트 색 및 해당 항목에 대 한 특성을 제공 합니다. 첫 번째 항목으로 목록에 자리 표시자 색 항목을 제공 하는 가장 쉬운 방법은이 참조 되지 않은 항목을 처리 하는 경우

## <a name="implement-custom-colorable-items"></a>사용자 지정 색 항목 구현

1. 예를 들어 키워드, 연산자 및 식별자 언어로 색이 지정 될 해야 무엇을 정의 합니다.

2. 이러한 색 항목의 열거형을 만듭니다.

3. 파서 또는 열거 된 값을 사용 하 여 스캐너에서 반환 되는 토큰 형식에 연결 합니다.

    예를 들어, 토큰 형식을 나타내는 값을 사용자 지정 색 항목 열거에 동일한 값을 수 있습니다.

4. 구현의 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> 에서 메서드에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 개체, 특성 목록에 해당 하는 파서 또는 스캐너에서 반환 되는 토큰 형식에 사용자 지정 색 항목 열거형의 값으로 입력 합니다.

5. 구현 하는 동일한 클래스에는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> 인터페이스를 구현 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> 인터페이스와 해당 두 메서드를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 및 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>합니다.

6. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 인터페이스를 구현합니다.

7. 24 비트 또는 높은 색 값을 지원 하려는 경우 구현할 수도 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 인터페이스입니다.

8. 언어 서비스 개체를 포함 하는 목록을 만듭니다 프로그램 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 개체가 프로그램 파서 또는 스캐너를 식별할 수 있습니다 각 색 항목에 대해 하나씩 들어 있습니다.

    사용자 지정 색 항목 열거의 해당 값을 사용 하 여 목록의 각 항목에 액세스할 수 있습니다. 목록에 열거형 값을 인덱스로 사용 합니다. 목록의 첫 번째 항목을 액세스 하지 않는다는, 기본 텍스트에 해당 하므로 스타일을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 항상 자체를 처리 합니다. 자리 표시자 색 항목을 목록 맨 앞에 삽입 하 여이 보완할 수 있습니다.

9. 구현에는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> 메서드를 사용자 지정 색 항목 목록의 항목 개수를 반환 합니다.

10. 구현에는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> 메서드를 목록에서 요청 된 색 항목을 반환 합니다.

    구현 하는 방법의 예는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> 하 고 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 인터페이스를 참조 하세요. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.

## <a name="see-also"></a>참고자료
- [레거시 언어 서비스의 모델](../../extensibility/internals/model-of-a-legacy-language-service.md)
- [사용자 지정 편집기의 구문 색 지정](../../extensibility/syntax-coloring-in-custom-editors.md)
- [레거시 언어 서비스의 구문 색 지정](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)
- [구현 구문 색 지정](../../extensibility/internals/implementing-syntax-coloring.md)
- [방법: 기본 제공 색 항목 사용](../../extensibility/internals/how-to-use-built-in-colorable-items.md)