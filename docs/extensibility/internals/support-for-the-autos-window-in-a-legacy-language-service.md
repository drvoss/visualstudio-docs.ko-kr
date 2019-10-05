---
title: 레거시 언어 서비스의 자동 창에 대 한 지원 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2842cb7a11765f0d460681dee0187c62ff31061c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66309835"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>레거시 언어 서비스의 자동 창 지원
합니다 **자동** 변수 등 디버깅 중인 프로그램 (되거나 중단점 또는 예외)를 일시 중지 되 면 범위에 있는 매개 변수 식 창에 표시 됩니다. 로컬 또는 전역 변수 및 매개 변수는 로컬 범위에서 변경 된 식이 포함할 수 있습니다. 합니다 **자동** 창 클래스, 구조체 또는 다른 일종의 인스턴스화를 포함할 수도 있습니다. 식 계산기를 평가할 수 있는 모든 항목에 잠재적으로 표시할 수는 **자동** 창입니다.

 에 대 한 직접 지원 (MPF)에서 관리 되는 패키지 프레임 워크를 **자동** 창입니다. 그러나 재정의 하는 경우는 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> 메서드를 제공 하는 식의 목록을 반환할 수 있습니다 합니다 **자동** 창입니다.

## <a name="implementing-support-for-the-autos-window"></a>자동 창에 대 한 지원 구현
 지원 하기 위해 필요한 모든 합니다 **자동** 창을 구현 하는 것을 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스. 식에 표시 되어야 하는 소스 파일의 위치를 지정 된 구현을 결정 해야 합니다 **자동** 창입니다. 메서드는 각 문자열 단일 식을 나타내는 문자열의 목록을 반환 합니다. 반환 값 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 식 목록에 포함 되어 있음을 나타냅니다 동안 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> 표시할 식이 없습니다 됨을 나타냅니다.

 반환 된 실제 식은 변수 또는 코드에서 해당 위치에 표시 되는 매개 변수 이름입니다. 이러한 이름은 다음에 표시 되는 형식과 값을 얻으려면 식 계산기에 전달 되는 **자동** 창입니다.

### <a name="example"></a>예제
 다음 예제에서는 구현을 보여 줍니다.는 <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> 에서 식의 목록을 가져오는 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 구문 분석 이유를 사용 하 여 메서드 <xref:Microsoft.VisualStudio.Package.ParseReason>. 로 래핑되는 식의 각를 `TestVsEnumBSTR` 구현 하는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> 인터페이스.

 `GetAutoExpressionsCount` 하 고 `GetAutoExpression` 메서드는 사용자 지정에 `TestAuthoringSink` 개체 및이 예제를 지원 하기 위해 추가 되었습니다. 에 추가 하는 식에는 한 가지 방법은 나타내는 합니다 `TestAuthoringSink` 파서에서 개체 (호출 하 여를 <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> 메서드) 파서를 외부에서 액세스할 수 합니다.

```csharp
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override int GetProximityExpressions(IVsTextBuffer buffer,
                                                    int line,
                                                    int col,
                                                    int cLines,
                                                    out IVsEnumBSTR ppEnum)
        {
            int retval = VSConstants.E_NOTIMPL;
            ppEnum = null;
            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.Autos,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        retval = VSConstants.S_FALSE;
                        int spanCount = sink.GetAutoExpressionsCount();
                        if (spanCount > 0) {
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();
                            for (int i = 0; i < spanCount; i++)
                            {
                                TextSpan span;
                                sink.GetAutoExpression(i, out span);
                                string expression = src.GetText(span.iStartLine,
                                                                span.iStartIndex,
                                                                span.iEndLine,
                                                                span.iEndIndex);
                                bstrList.AddString(expression);
                            }
                            ppEnum = bstrList;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```