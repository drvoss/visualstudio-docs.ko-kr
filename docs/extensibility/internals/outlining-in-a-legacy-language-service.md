---
title: 레거시 언어 서비스의 개요 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7af8ab4615cff7462a47dfb11b193660eb62274c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314876"
---
# <a name="outlining-in-a-legacy-language-service"></a>레거시 언어 서비스의 개요 표시
개요 개요 또는 개요로 복잡 한 프로그램을 축소할 수 있습니다. 예를 들어 C#의 모든 메서드는 메서드 시그니처를 보여 주는 단일 줄으로 축소할 수 있습니다. 또한 구조체와 클래스 구조 및 클래스의 이름만 표시 하도록 축소할 수 있습니다. 단일 메서드 내에서 복잡 한 논리 축소할 수 있습니다와 같은 문 첫 번째 줄만 표시 하 여 전체 흐름을 나타내기 위해 `foreach`, `if`, 및 `while`합니다.

 레거시 언어 서비스는 VSPackage의 일부로 구현 됩니다 있지만 MEF 확장을 사용 하는 언어 서비스 기능을 구현 하는 최신 방법입니다. 자세한 내용을 알아보려면 참조 [연습: 개요](../../extensibility/walkthrough-outlining.md)를 참조하세요.

> [!NOTE]
> 편집기를 사용 하 여 새 API 최대한 빨리 시작 하는 것이 좋습니다. 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.

## <a name="enabling-support-for-outlining"></a>개요에 대 한 지원을 사용 하도록 설정
 `AutoOutlining` 레지스트리 항목이 자동 개요 표시를 사용 하도록 설정 하려면 1로 설정 됩니다. 파일 로드 되거나 숨겨진된 영역을 식별 하 고 개요 문자 모양을 표시 하도록 변경 하는 경우 전체 소스를 구문 분석 설정의 자동 개요 표시 합니다. 개요 제어할 수도 있습니다 수동으로 사용자가 있습니다.

 값을 `AutoOutlining` 레지스트리 항목을 통해 얻을 수 있습니다를 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> 속성에는 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 클래스. 합니다 `AutoOutlining` 레지스트리 항목을 명명된 된 매개 변수를 사용 하 여 초기화할 수 있습니다 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 특성 (참조 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md) 세부 정보에 대 한).

## <a name="the-hidden-region"></a>숨겨진된 영역
 언어 서비스는 개요를 제공 하려면 숨겨진된 영역을 지원 해야 합니다. 이들은 확장 하거나 축소할 수 있는 텍스트의 범위입니다. 사용자 지정 기호 또는 중괄호와 같은 표준 언어 기호를 하 여 숨겨진된 영역을 구분할 수 있습니다. 예를 들어 C#에 `#region` / `#endregion` 숨겨진된 영역을 구분 하는 쌍.

 숨겨진된 영역으로 노출 되는 숨겨진된 영역 관리자가 관리 되는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 인터페이스입니다.

 숨겨진된 영역 사용 개요를 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> 인터페이스 및 숨겨진된 영역, 현재 표시 상태 및 범위를 축소 된 경우 표시할 배너의 범위를 포함 합니다.

 언어 서비스 파서를 사용 하는 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 숨겨진된 영역에 대 한 기본 동작을 사용 하 여 새 숨겨진된 영역을 추가 하는 방법 동안는 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> 메서드 윤곽선의 동작과 모양을 사용자 지정할 수 있습니다. 숨겨진된 영역 숨겨진된 영역 세션에 부여 되 면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 언어 서비스에 대 한 숨겨진된 영역을 관리 합니다.

 숨겨진된 영역 세션 소멸 될 때 확인 해야 할 경우 숨겨진된 영역 변경 되 면 또는 특정 숨겨진된 영역 표시 되는지 확인 해야 합니다. 클래스를 파생 해야 합니다 <xref:Microsoft.VisualStudio.Package.Source> 클래스 및 적절 한 메서드를 재정의 <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, 및 <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>각각.

### <a name="example"></a>예제
 모든 중괄호 쌍에 대해 숨겨진된 영역을 만드는 간단한 예는 다음과 같습니다. 언어는 중괄호 일치 및 일치 시킬 중괄호 중괄호를 포함 하 간주 됩니다 ({및}). 이 방법은 설명을 위한 용도로 합니다. 전체 구현은 사례의 전체 처리 해야 합니다. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>합니다. 설정 하는 방법을 보여이 줍니다 합니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> 우선 `true` 일시적으로 합니다. 대신 지정 하는 것을 `AutoOutlining` 명명 된 매개 변수와 `ProvideLanguageServiceAttribute` 언어 패키지에는 특성입니다.

 이 예제에서는 C# 주석, 문자열 및 리터럴에 대 한 규칙을 가정합니다.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>참고 항목
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)