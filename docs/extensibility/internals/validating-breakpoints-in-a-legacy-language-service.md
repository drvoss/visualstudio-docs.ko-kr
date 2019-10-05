---
title: 레거시 언어 서비스의 중단점 유효성 검사 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 177b0bb3fddebab6518a851bf8ce4c4d34d43897
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324569"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>레거시 언어 서비스의 중단점 유효성 검사
중단점 디버거에서 실행 되는 동안 특정 지점에서 프로그램 실행 중지 해야 함을 나타냅니다. 편집기에 중단점의 올바른 위치를 구성 하는 데 대 한 지식은 없는 사용자 소스 파일에서 줄 중단점을 배치 수 있습니다. 디버거를 시작할 때 실행 중인 프로그램에 적절 한 위치에 바인딩됩니다 (보류 중단점 라고 함)은 표시 된 중단점의 모든 나타납니다. 중단점의 유효성을 검사 했는지 한 번에 유효한 코드 위치 표시 합니다. 예를 들어, 메모 중단점 올바르지 소스 코드의 위치에 있는 코드 없이 있기 때문에 합니다. 디버거가 잘못 된 중단점을 해제합니다.

 언어 서비스에서 표시 되 고 소스 코드를 인식 하므로 디버거를 시작 하기 전에 중단점을 확인할 수 것입니다. 재정의할 수 있습니다는 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 중단점의 올바른 위치를 지정 하는 범위를 반환 하는 방법입니다. 중단점 위치는 계속 디버거를 시작할 경우 디버거에서 로드할 때까지 기다리지 않고 잘못 된 중단점의 사용자가 알림을 유효성이 검사 됩니다.

## <a name="implementing-support-for-validating-breakpoints"></a>중단점 유효성 검사에 대 한 지원 구현

- <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 메서드에 중단점의 위치를 제공 됩니다. 구현에는 위치가 유효 하 고 줄 위치를 사용 하 여 관련 코드를 식별 하는 텍스트 범위를 반환 하 여이 중단점이 나타내는 있는지 여부를 결정 해야 합니다.

- 반환 <xref:Microsoft.VisualStudio.VSConstants.S_OK> 위치가 유효 하면 또는 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> 유효 하지 않은 경우.

- 중단점이 올바르면 중단점 함께 텍스트 범위를 강조 표시 됩니다.

- 중단점 올바르지 않으면 오류 메시지가 상태 표시줄에 나타납니다.

### <a name="example"></a>예제
 구현을 보여 주는이 예제는 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 지정 된 위치 (해당 되는 경우) 코드의 범위를 가져오려면 파서를 호출 하는 메서드입니다.

 이 예에서는 추가 했다고 가정를 `GetCodeSpan` 메서드를 합니다 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 확인 하는 텍스트 범위를 반환 하는 클래스 `true` 중단점이 올바르면 위치인 경우.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

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
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
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

## <a name="see-also"></a>참고 항목
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)