---
title: 레거시 언어 서비스의 중괄호 일치 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a535fc479fe5cc398d09d7aa9e47a3c91fa97f38
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309177"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>레거시 언어 서비스의 중괄호 일치
중괄호 일치 괄호와 중괄호와 같이 함께 수행 해야 하는 언어 요소를 추적 하는 개발자는 데 도움이 됩니다. 개발자가 닫는 중괄호를 여는 중괄호 강조 표시 됩니다.

 쌍 및 삼중 쌍 이라는 두 가지 또는 세 개의 동시 발생 요소를 일치 시킬 수 있습니다. 삼중 쌍은 세 개의 동시 발생 요소의 집합입니다. 예를 들어 C#에서 `foreach` 문을 forms 3: `foreach()`, `{`, 및 `}`합니다. 세 요소 모두에 닫는 중괄호를 입력할 때 강조 표시 됩니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 중괄호 일치를 구현 하는 새로운 방법에 대 한 자세한 참조 [연습: 괄호 일치 표시](../../extensibility/walkthrough-displaying-matching-braces.md)합니다.

> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 클래스는 두 쌍을 지원 하 고 사용 하 여 데이터 집합을 가져와 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> 및 <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> 메서드.

## <a name="implementation"></a>구현
 언어 서비스는 언어에서 일치 하는 모든 요소를 식별 하 고 다음 모든 일치 하는 쌍을 찾는 해야 합니다. 구현 하 여 일반적으로 이렇게 <xref:Microsoft.VisualStudio.Package.IScanner> 일치 하는 언어 및 사용 하 여 다음을 검색 하는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 요소와 일치 하는 방법입니다.

 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 호출 스캐너 줄을 토큰화 하는 캐럿 바로 전에 토큰을 반환 합니다. 스캐너 토큰 트리거 값을 설정 하 여 언어 요소 쌍이 발견 된 나타냅니다 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 현재 토큰에 있습니다. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 메서드 호출을 <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> 메서드를 호출 하는 <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> 구문 분석 이유 값을 사용 하 여 메서드 <xref:Microsoft.VisualStudio.Package.ParseReason> 일치 하는 언어 요소를 찾는. 일치 하는 언어 요소가 발견 되 면 두 요소 모두 강조 표시 됩니다.

 중괄호 입력가 중괄호 강조 표시를 트리거합니다 하는 방법의 설명은 참조 하세요. 합니다 *예제에서는 구문 분석 작업이* 문서의 섹션 [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)합니다.

## <a name="enable-support-for-brace-matching"></a>중괄호 일치에 대 한 지원을 사용 하도록 설정
 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 특성을 설정할 수는 **MatchBraces**를 **MatchBracesAtCaret**, 및 **ShowMatchingBrace** 해당 속성을 설정 하는 레지스트리 항목 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 클래스입니다. 또한 사용자가 언어 기본 설정 속성을 설정할 수 있습니다.

|레지스트리 항목|속성|설명|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|사용 하도록 설정 중괄호 일치 합니다.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|이동 캐럿으로 중괄호 일치를 사용 하도록 설정 합니다.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|일치 하는 중괄호를 강조 표시합니다.|

## <a name="match-conditional-statements"></a>일치 조건 문
 같은 조건문을 일치 시킬 수 있습니다 `if`, `else if`, 및 `else`, 또는 `#if`를 `#elif`를 `#else`, `#endif`, 구분 기호가 일치와 같은 방식에서입니다. 서브 클래스 수를 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 클래스와 일치 하는 요소의 내부 배열에 대 한 구분 기호 및 걸쳐 있는 텍스트를 추가할 수 있는 메서드를 제공 합니다.

## <a name="set-the-trigger"></a>트리거 설정
 다음 예제에서는 일치 하는 괄호, 검색할 중괄호 및 대괄호, 스캐너에서에 대 한 트리거를 설정 하는 방법을 보여 줍니다. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> 메서드를 <xref:Microsoft.VisualStudio.Package.Source> 트리거를 검색 하 고 일치 하는 쌍을 찾을 수 있는 파서를 호출 하는 클래스 (참조는 *일치 하는 항목을 찾은* 이 문서의 섹션). 이 예제는 설명 목적 으로만 제공 됩니다. 스캐너는 메서드가 포함 되어 있는지 가정 `GetNextToken` 식별 하 고 텍스트 줄에서 토큰을 반환 합니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>중괄호 일치
 다음은 언어 요소를 일치 하는 간단한 예제 `{ }`, `( )`, 및 `[ ]`, 해당 범위를 추가 하 고는 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 개체입니다. 이 방법은 소스 코드를 구문 분석에 권장 되는 방법은 아닙니다. 설명 목적 으로만 제공 됩니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>참고자료
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)