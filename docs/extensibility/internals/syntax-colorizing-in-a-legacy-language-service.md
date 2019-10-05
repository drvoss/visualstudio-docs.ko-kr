---
title: 레거시 언어 서비스의 구문 색 지정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: edbb7f2dca6bc0bc28a328276680dd9e273f4176
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331141"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>레거시 언어 서비스의 구문 색 지정
구문 색 지정에는 서로 다른 색 및 스타일에 소스 파일에 표시 되는 프로그래밍 언어의 다양 한 요소를 발생 시키는 기능입니다. 이 기능을 지원 하려면 파서 또는 어휘 요소 또는 파일에는 토큰의 형식을 식별할 수는 스캐너를 제공 해야 합니다. 다양 한 언어 키워드, 구분 기호 (예: 괄호 또는 중괄호) 및 주석을 가지에서 색을 지정 하 여 구분 합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 자세한 내용을 참조 하세요 [편집기 및 언어 서비스 확장](../../extensibility/extending-the-editor-and-language-services.md)합니다.

> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="implementation"></a>구현
 색 지정을 지원 하려면 관리 되는 패키지 프레임 워크 (MPF)를 포함 합니다 <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스를 구현 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 인터페이스입니다. 이 클래스와 상호 작용 하는 <xref:Microsoft.VisualStudio.Package.IScanner> 토큰 및 색을 확인 하려면. 스캐너에 대 한 자세한 내용은 참조 하세요. [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)합니다. <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스에서 다음 색 정보를 사용 하 여 토큰의 각 문자를 표시 하 고 소스 파일을 표시 하는 편집기에 해당 정보를 반환 합니다.

 편집기로 반환 되는 색 정보는 색 항목 목록에는 인덱스입니다. 각 색 항목 색 값 및 글꼴 특성 집합이 굵게 지정 또는 취소선 합니다. 편집기의 기본 언어 서비스를 사용할 수 있는 색 항목 집합을 제공 합니다. 각 토큰 형식에 대 한 적절 한 색 인덱스를 지정 해야 할 됩니다. 그러나 토큰에 대 한 사용자 지정 색 항목을 제공한 인덱스 집합을 제공 하 고 사용자 고유의 기본 목록 대신 색 항목 목록을 참조할 수 있습니다. 설정 해야 합니다 `RequestStockColors` 레지스트리 항목을 0 (지정 하지 마십시오를 `RequestStockColors` 모든 항목) 사용자 지정 색을 지원 하기 위해. 이 레지스트리 항목을 명명된 된 매개 변수를 사용 하 여 설정할 수 있습니다는 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 사용자 정의 특성입니다. 언어 서비스를 등록 하 고 해당 옵션 설정에 대 한 자세한 내용은 참조 하세요. [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)합니다.

## <a name="custom-colorable-items"></a>사용자 지정 색 항목
 사용자 고유의 사용자 지정 색 항목을 제공 하려면 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> 및 <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스입니다. 첫 번째 방법은 언어 서비스가 지 원하는 사용자 지정 색 항목 수를 반환 하 고 두 번째 인덱스 별로 사용자 지정 색 항목을 가져옵니다. 사용자 지정 색 항목의 기본 목록을 만듭니다. 언어 서비스의 생성자에서 각 색 항목 이름으로 제공 하기만 하면 됩니다. Visual Studio는 사용자가 다양 한 색 항목을 선택 하는 경우를 자동으로 처리 합니다. 이 이름이 표시 됩니다는 **글꼴 및 색** 속성 페이지를 **옵션** 대화 상자 (Visual Studio에서 사용할 수 있습니다 **도구** 메뉴)이이 이름을 결정 하 고 사용자가 재정의 되는 색입니다. 사용자의 선택 레지스트리에서 캐시에 저장 되 고 색 이름으로 액세스 합니다. 합니다 **글꼴 및 색** ; 언어 이름의 각 색 이름 앞에 사용자 지정 색을 그룹화 할 수 있습니다 있도록 알파벳 순서로 색 이름 중 모든 속성 페이지 나열 예를 들어, "**TestLanguage-주석**"및"**TestLanguage 키워드가**"입니다. 형식에 의해 색 항목을 그룹화 할 수 있습니다 또는 " **(TestLanguage) 주석**"및"**키워드 (TestLanguage)** "입니다. 언어 이름으로 그룹화는 것이 좋습니다.

> [!CAUTION]
> 기존 색 항목 이름과 충돌 하지 않도록 하려면 색 항목 이름에 언어 이름을 포함 하는 것이 좋습니다.

> [!NOTE]
> 개발 중에 색 중 하나의 이름을 변경한 경우에 Visual Studio에서 처음으로 액세스 된 색을 생성 하는 캐시를 다시 설정 해야 합니다. 실행 하 여 수행할 수는 **실험적 하이브 재설정** Visual Studio SDK 프로그램 메뉴에서 명령을 합니다.

 색 항목 목록에서 첫 번째 항목 참조 되지 않는 참고 합니다. Visual Studio에는 항상 기본 텍스트 색 및 해당 항목에 대 한 특성을 제공합니다. 이 처리 하는 가장 쉬운 첫 번째 항목으로 자리 표시자 색 항목을 제공 하는 경우

### <a name="high-color-colorable-items"></a>하이 컬러 색 항목
 색 항목을 통해 24 비트 또는 높은 색 값을 지원할 수도 있습니다는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 인터페이스입니다. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> 지원 클래스를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> 일반적인 색과 함께 생성자의 인터페이스와 24 비트 색을 지정 합니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Package.ColorableItem> 클래스를 참조하십시오. 아래 예제에서는 주석 및 키워드에 대 한 24 비트 색을 설정 하는 방법을 보여 줍니다. 24 비트 색 및 사용자의 데스크톱;에서 지원 되는 경우 24 비트 색이 사용 됩니다. 그렇지 않은 경우 일반 텍스트 색이 사용 됩니다.

 언어;에 대 한 기본 색을입니다 사용자는 원하는 대로 자유롭게이 색상을 변경할 수 있습니다.

### <a name="example"></a>예제
 이 예제에서는 선언 하 고 사용 하 여 사용자 지정 색 항목 배열을 채우는 방법을 보여 줍니다는 <xref:Microsoft.VisualStudio.Package.ColorableItem> 클래스입니다. 이 예에서는 24 비트 색을 사용 하는 키워드와 주석 색을 설정 합니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private ColorableItem[] m_colorableItems;

        TestLanguageService() : base()
        {
            m_colorableItems = new ColorableItem[] {
                new ColorableItem("TestLanguage - Text",
                                  "Text",
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.Empty,
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT),
                new ColorableItem("TestLanguage - Keyword",
                                  "Keyword",
                                  COLORINDEX.CI_MAROON,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.FromArgb(192,32,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_BOLD),
                new ColorableItem("TestLanguage - Comment",
                                  "Comment",
                                  COLORINDEX.CI_DARKGREEN,
                                  COLORINDEX.CI_LIGHTGRAY,
                                  System.Drawing.Color.FromArgb(32,128,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT)
                // ...
                // Add as many colorable items as you want to support.
            };
        }
    }
}
```

## <a name="the-colorizer-class-and-the-scanner"></a>Colorizer 클래스와 스캐너
 기본 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스에는 <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> 메서드는 instantiantes는 <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스입니다. 반환 되는 스캐너를 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 메서드에 전달 되는 <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스 생성자입니다.

 구현 해야 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> 고유한 버전의 메서드는 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스. <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스 스캐너를 사용 하 여 모든 토큰 색 정보를 얻을 수 있습니다.

 스캐너를 채우는 데 필요한를 <xref:Microsoft.VisualStudio.Package.TokenInfo> 구조체 모든 토큰에 대 한 해당 찾습니다. 이 구조는 토큰 범위를 차지 색 인덱스를 사용 하려면 같은 정보를 포함 유형을 토큰 및 토큰 트리거 (참조 <xref:Microsoft.VisualStudio.Package.TokenTriggers>). 범위 및 색 인덱스만에서 색 지정에 대 한 필요를 <xref:Microsoft.VisualStudio.Package.Colorizer> 클래스입니다.

 색 인덱스가에 저장 합니다 <xref:Microsoft.VisualStudio.Package.TokenInfo> 구조에서 값은 일반적으로 <xref:Microsoft.VisualStudio.Package.TokenColor> 키워드 및 연산자와 같은 다양 한 언어 요소에 해당 하는 명명 된 인덱스의 수를 제공 하는 열거형. 사용자 지정 색 항목 목록 일치 항목에 표시 된 <xref:Microsoft.VisualStudio.Package.TokenColor> 열거형을 사용할 수 있습니다만 열거형 색으로 각 토큰에 대 한 합니다. 그러나 추가 색 항목이 있는 경우 기존 값을 지정 된 순서로 사용 하지 않으려는 경우 해당 목록에 적절 한 인덱스를 반환 하 고 요구에 맞게 사용자 지정 색 항목 목록에 정렬할 수 있습니다. 인덱스를 캐스팅 해야는 <xref:Microsoft.VisualStudio.Package.TokenColor> 에 저장 하는 경우는 <xref:Microsoft.VisualStudio.Package.TokenInfo> ; 구조체 [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] 인덱스만 표시 됩니다.

### <a name="example"></a>예제
 다음 예제에서는 스캐너 세 토큰 형식을 식별할 수 있습니다 하는 방법을 보여 줍니다: 숫자, 문장 부호, 및 식별자 (이외의 모든 숫자 또는 문장 부호). 이 예에서는 설명 목적 으로만 제공 되며 포괄적인 파서 및 검사기 구현을 나타내지 않습니다. 있다고 가정 하는 `Lexer` 클래스를 `GetNextToken()` 문자열을 반환 하는 메서드입니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    private Lexer lex;

    public class TestScanner : IScanner
    {
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                }
                else if (Char.IsNumber(firstChar))
                {
                    tokenInfo.Type = TokenType.Literal;
                    tokenInfo.Color = TokenColor.Number;
                }
                else
                {
                    tokenInfo.Type = TokenType.Identifier;
                    tokenInfo.Color = TokenColor.Identifier;
                }
            }
            return foundToken;
        }
```

## <a name="see-also"></a>참고 항목
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)