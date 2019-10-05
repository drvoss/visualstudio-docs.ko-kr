---
title: 레거시 언어 Service2의 매개 변수 정보 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d1fddc99c40e2472688a25ade121c2c762ade5da
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437927"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>레거시 언어 서비스의 매개 변수 정보
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

IntelliSense 매개 변수 정보는 메서드 매개 변수 목록에 대 한 문자 (일반적으로 여는 괄호)를 시작 하는 사용자가 매개 변수 목록 메서드 시그니처를 표시 하는 도구 설명입니다. 각 매개 변수를 입력 매개 변수 구분 기호 (쉼표)를 입력 하 고 도구 설명 굵게 표시 된 다음 매개 변수를 표시 하도록 업데이트 됩니다.  
  
 관리 되는 패키지 프레임 워크 (MPF) 클래스는 관리 매개 변수 정보 도구 설명에 대 한 지원을 제공 합니다. 매개 변수 시작 매개 변수 다음으로, 및 매개 변수 끝 문자 및 해당 메서드 서명과 연결 된 해당 매개 변수 목록을 제공 해야 파서를 검색 해야 합니다.  
  
 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 자세한 내용을 참조 하세요 [편집기 및 언어 서비스 확장](../../extensibility/extending-the-editor-and-language-services.md)합니다.  
  
> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.  
  
## <a name="implementation"></a>구현  
 파서가 트리거 값을 설정 해야 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 매개 변수 목록 시작 문자 (종종 여는 괄호)를 발견할 때 설정 됩니다. 설정 해야는 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 매개 변수 구분 기호 (종종 쉼표)를 발견 하면 트리거. 이렇게 하면 업데이트할 굵게 표시 된 다음 매개 변수를 표시 하는 매개 변수 정보 도구 설명 합니다. 파서가 트리거 값을 설정 해야 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 때 경우 매개 변수 목록 끝 문자 (종종 닫는 괄호)를 찾습니다.  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> 트리거 값에 대 한 호출을 시작 합니다 <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> 메서드를 호출 하는 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 의 구문 분석 이유인 메서드 파서 <xref:Microsoft.VisualStudio.Package.ParseReason>합니다. 파서는 식별자 매개 변수 목록에는 문자 시작 전에 인식할 수 있는 메서드 이름을 하다 고 결정을에서 메서드 시그니처를 일치 하는 목록을 반환 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체입니다. 모든 메서드 시그니처 발견 된 경우 목록에서 첫 번째 서명을 사용 하 여 매개 변수 정보 도구 설명이 표시 됩니다. 이 도구 설명에이 서명의 자세히가 입력 한 대로 업데이트 됩니다. 매개 변수 목록 끝 문자를 입력할 때 매개 변수 정보 도구 설명 보기에서 제거 됩니다.  
  
> [!NOTE]
> 매개 변수 정보 도구 설명에 형식이 제대로 위해이 속성에서 재정의 해야 합니다는 <xref:Microsoft.VisualStudio.Package.Methods> 적절 한 문자를 제공 하는 클래스입니다. 기본 <xref:Microsoft.VisualStudio.Package.Methods> 클래스 가정 하는 C#-스타일 메서드 시그니처입니다. 참조 된 <xref:Microsoft.VisualStudio.Package.Methods> 수행할 수 있는 방법을 대 한 세부 정보에 대 한 클래스입니다.  
  
## <a name="enabling-support-for-the-parameter-info"></a>매개 변수 정보에 대 한 지원을 사용 하도록 설정  
 를 지원 하기 위해 매개 변수 정보 도구 설명 설정 해야 합니다는 `ShowCompletion` 라는 매개 변수를 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 를 `true`합니다. 언어 서비스에서이 레지스트리 항목의 값을 읽고 여 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> 속성입니다.  
  
 또한 합니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> 속성으로 설정 되어 있어야 `true` 매개 변수 정보 도구 설명에 표시 합니다.  
  
### <a name="example"></a>예제  
 매개 변수 목록 문자를 검색 하 고 적절 한 트리거를 설정 하는 간단한 예는 다음과 같습니다. 이 예제는 설명 목적 으로만 제공 됩니다. 스캐너는 메서드가 포함 되어 있는지 가정 `GetNextToken` 식별 하 고 텍스트 줄에서 토큰을 반환 합니다. 예제 코드는 올바른 종류의 문자가 발견 될 때마다 간단히 트리거를 설정 합니다.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestScanner : IScanner  
    {  
        private Lexer lex;  
        private const char parameterListStartChar = '(';  
        private const char parameterListEndChar   = ')';  
        private const char parameterNextChar      = ',';  
  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                foundToken = true;  
                char c = token[0];  
                if (Char.IsPunctuation(c))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                    tokenInfo.EndIndex = index;  
  
                    if (c == parameterListStartChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;  
                    }  
                    else if (c == parameterListNextChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;  
                    else if (c == parameterListEndChar)  
                    {  
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;  
                    }  
                }  
            return foundToken;  
        }  
    }  
}  
```  
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>파서에서 매개 변수 정보 도구 설명이 지원  
 합니다 <xref:Microsoft.VisualStudio.Package.Source> 클래스의 내용에 대 한 가정을 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 및 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 매개 변수 정보 도구 설명이 표시 되 고 업데이트 하는 경우 클래스입니다.  
  
- 파서를 지정 하는 <xref:Microsoft.VisualStudio.Package.ParseReason> 매개 변수 목록 시작 문자를 입력 하는 경우.  
  
- 지정 된 위치는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 개체가 매개 변수 목록 시작 문자 직후입니다. 파서를 배치 하 고 사용 중인 버전에서 목록에 저장 하는 모든 메서드 선언에서 사용할 수 있는 서명을 수집 해야 합니다는 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 개체입니다. 이 목록에 메서드 이름, 메서드 형식 (또는 반환 형식) 및 가능한 매개 변수 목록입니다. 이 목록은 메서드 서명 또는 서명 매개 변수 정보 도구 설명에 표시할 나중에 검색 됩니다.  
  
  파서가 다음 지정한 줄을 구문 분석 해야 합니다는 <xref:Microsoft.VisualStudio.Package.ParseRequest> 사용자까지 진행 뿐만 아니라 입력 되는 메서드의 이름을 수집 하는 개체는 매개 변수를 입력 합니다. 메서드의 이름을 전달 하 여 이렇게를 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> 메서드를 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 개체를 호출 하 고는 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> 메서드 매개 변수 목록 시작 문자는 구문 분석 호출를 <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> 메서드 때 매개 변수 목록 다음 문자는 구문 분석 되 고 및 마지막으로 호출 된 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> 메서드 매개 변수 목록 끝 문자를 구문 분석할 때. 사용 하는 이러한 메서드 호출의 결과 <xref:Microsoft.VisualStudio.Package.Source> 매개 변수 정보 도구 설명을 적절 하 게 업데이트 하는 클래스입니다.  
  
### <a name="example"></a>예제  
 사용자가 입력 하는 텍스트 줄을 다음과 같습니다. 아래 줄 번호 (구문 분석 이동 왼쪽에서 오른쪽으로 가정) 줄의 해당 위치에 파서에서 단계를 수행 하는 것을 나타냅니다. 가정 하는 줄 앞에 나오는 모든 이미 구문 분석 되었습니다 "testfunc" 메서드 시그니처를 포함 하 여 메서드 서명에입니다.  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 파서를 사용 하는 단계는 다음과 같습니다.  
  
1. 파서에서 호출 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> "testfunc" 텍스트를 사용 하 여 합니다.  
  
2. 파서에서 호출 <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>합니다.  
  
3. 파서에서 호출 <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>합니다.  
  
4. 파서에서 호출 <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>합니다.
