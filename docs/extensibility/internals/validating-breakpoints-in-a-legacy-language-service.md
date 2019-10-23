---
title: 레거시 언어 서비스에서 중단점 유효성 검사 | Microsoft Docs
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
ms.openlocfilehash: e7c46473610c96779d0c54e06e82cf884216b13b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722017"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>레거시 언어 서비스의 중단점 유효성 검사
중단점은 프로그램 실행이 디버거에서 실행 되는 동안 특정 지점에서 중지 되어야 함을 나타냅니다. 편집기는 중단점에 대해 유효한 위치를 구성 하는 항목에 대해 알지 못하므로 사용자는 소스 파일의 모든 줄에 중단점을 설정할 수 있습니다. 디버거를 실행 하면 표시 된 모든 중단점 (보류 중인 중단점 이라고 함)이 실행 중인 프로그램의 적절 한 위치에 바인딩됩니다. 중단점의 유효성을 검사 하 여 유효한 코드 위치를 표시 하는지 확인 합니다. 예를 들어 소스 코드의 해당 위치에는 코드가 없기 때문에 주석에서 중단점을 사용할 수 없습니다. 디버거가 잘못 된 중단점을 사용 하지 않도록 설정 합니다.

 언어 서비스는 표시 되는 소스 코드에 대해 알고 있으므로 디버거를 시작 하기 전에 중단점의 유효성을 검사할 수 있습니다. 중단점에 대 한 올바른 위치를 지정 하 여 범위를 반환 하도록 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 메서드를 재정의할 수 있습니다. 디버거가 시작 될 때 중단점 위치는 여전히 유효성이 검사 되지만 디버거가 로드 될 때까지 기다리지 않고 잘못 된 중단점에 대 한 알림이 사용자에 게 표시 됩니다.

## <a name="implementing-support-for-validating-breakpoints"></a>중단점 유효성 검사에 대 한 지원 구현

- @No__t_0 메서드에는 중단점의 위치가 제공 됩니다. 구현은 위치가 유효한 지 여부를 결정 해야 하며, 중단점의 줄 위치와 연결 된 코드를 식별 하는 텍스트 범위를 반환 하 여이를 나타냅니다.

- 위치가 유효 하면 <xref:Microsoft.VisualStudio.VSConstants.S_OK>을 반환 하 고, 유효 하지 않은 경우 <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> 합니다.

- 중단점이 올바르면 텍스트 범위가 중단점과 함께 강조 표시 됩니다.

- 중단점이 잘못 된 경우 상태 표시줄에 오류 메시지가 표시 됩니다.

### <a name="example"></a>예제
 이 예제에서는 지정 된 위치에서 코드 범위 (있는 경우)를 가져오기 위해 파서를 호출 하는 <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> 메서드의 구현을 보여 줍니다.

 이 예제에서는 텍스트 범위의 유효성을 검사 하 고 유효한 중단점 위치인 경우 `true`를 반환 하는 `GetCodeSpan` 메서드를 <xref:Microsoft.VisualStudio.Package.AuthoringSink> 클래스에 추가 했다고 가정 합니다.

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

## <a name="see-also"></a>참조
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)