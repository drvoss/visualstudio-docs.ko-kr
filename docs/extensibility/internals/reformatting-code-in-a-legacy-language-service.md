---
title: 레거시 언어 서비스의 코드 서식 다시 지정 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16130191eb6a4d8b6d7703a05aaf3271f8c739f5
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67891129"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>레거시 언어 서비스의 코드 서식 다시 지정

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 소스 코드 들여쓰기 및 공백 사용을 정규화 하 여 서식이 다시 지정 될 수 있습니다. 이 삽입 또는 공백이 나 탭에서 각 줄의 시작 부분을 제거, 줄 사이 새 줄 추가 공간을 탭 또는 탭을 공백으로 바꿉니다 포함할 수 있습니다.

> [!NOTE]
> 영향을 줄 바꿈 문자를 삭제 또는 삽입 중단점 및 책갈피 등의 마커를 줄 수 있지만 공백 또는 탭 추가 및 제거 표식에 영향을 주지 않습니다.

선택 하 여 사용자가 다시 포맷 작업을 시작할 수 있습니다 **선택 영역 서식** 또는 **문서 서식** 에서 합니다 **고급** 메뉴에서를 **편집**메뉴. 코드 조각 또는 특정 문자를 삽입할 때 다시 포맷 작업을 트리거할 수도 있습니다. 예를 들어 C#에서는 닫는 중괄호를 입력 하면 일치 하는 여는 중괄호 및 닫는 중괄호 사이의 모든 아닌 경우 적절 한 수준으로 자동으로 들여쓰기

때 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 보냅니다 합니다 **선택 영역 서식** 또는 **문서 서식** 언어 서비스에 명령을 <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스를 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 에서 메서드를 <xref:Microsoft.VisualStudio.Package.Source> 클래스. 재정의 해야 하는 서식 지정을 지원 하기는 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 코드 서식 지정 고유한 메서드 및 공급 합니다.

## <a name="enabling-support-for-reformatting"></a>다시 포맷 하는 것에 대 한 지원을 사용 하도록 설정

형식 지정을 지원 하는 `EnableFormatSelection` 의 매개 변수를 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 로 변경 해야 `true` VSPackage를 등록 하는 경우. 이 설정 된 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> 속성을 `true`입니다. <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> 메서드는이 속성의 값을 반환 합니다. True를 반환 하는 경우는 <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스는 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>합니다.

## <a name="implementing-reformatting"></a>다시 포맷 구현

서식을 다시 지정을 구현 하려면 클래스에서 파생 해야 합니다 <xref:Microsoft.VisualStudio.Package.Source> 클래스를 재정의 합니다 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 메서드. 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 서식을 지정 하는 범위를 설명 하는 개체 및 <xref:Microsoft.VisualStudio.Package.EditArray> 개체 범위에 대 한 편집 내용을 저장 합니다. 이 범위는 전체 문서 수 있음을 참고 합니다. 그러나가 범위에 대 한 여러 변경 될 수 있으므로 모든 변경 내용을 단일 작업으로 되돌릴 수 있어야 합니다. 이렇게 하려면 모든 변경 내용을 래핑하는 <xref:Microsoft.VisualStudio.Package.CompoundAction> 개체 (이 항목의 "CompoundAction 클래스를 사용 하 여" 섹션 참조).

### <a name="example"></a>예제

다음 예제에서는 있습니다 않는 공백 모든 쉽표 뒤 선택 항목에서 쉼표 뒤에 탭 또는 줄의 끝을 확인 합니다. 후행 공백 줄에는 마지막 쉼표를 삭제 한 후입니다. 이 메서드를 호출 하는 방법을 보려면이 항목의 "CompoundAction 클래스를 사용 하 여" 섹션을 참조 합니다 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 메서드.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        private void DoFormatting(EditArray mgr, TextSpan span)
        {
            // Make sure there is one space after every comma unless followed
            // by a tab or comma is at end of line.
            IVsTextLines pBuffer = GetTextLines();
            if (pBuffer != null)
            {
                int    startIndex = span.iStartIndex;
                int    endIndex   = 0;
                string line       = "";
                // Loop over all lines in span
                for (int i = span.iStartLine; i <= span.iEndLine; i++)
                {
                    if (i < span.iEndLine)
                    {
                        pBuffer.GetLengthOfLine(i, out endIndex);
                    }
                    else
                    {
                        endIndex = span.iEndIndex;
                    }
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);

                    if (line.Length > 0)
                    {
                        int index = 0;
                        // Loop over all commas in line
                        while ((index = line.IndexOf(',', index)) != -1)
                        {
                            int spaceIndex = index + 1;
                            // Determine how many spaces after comma
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')
                            {
                                ++spaceIndex;
                            }

                            int      spaceCount      = spaceIndex - (index + 1);
                            string   replacementText = " ";
                            bool     fDoEdit         = true;
                            TextSpan editTextSpan    = new TextSpan();

                            editTextSpan.iStartLine  = i;
                            editTextSpan.iEndLine    = i;
                            editTextSpan.iStartIndex = index + 1;

                            if (spaceIndex == line.Length)
                            {
                                if (spaceCount > 0)
                                {
                                    // Delete spaces after a comma at end of line
                                    editTextSpan.iEndIndex = spaceIndex;
                                    replacementText = "";
                                }
                                else
                                {
                                    // Otherwise, do not add spaces if comma is
                                    // at end of line.
                                    fDoEdit = false;
                                }
                            }
                            else if (spaceCount == 0)
                            {
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')
                                {
                                    // Do not insert space if a tab follows
                                    // a comma.
                                    fDoEdit = false;
                                }
                                else
                                {
                                    // No space after comma so add a space.
                                    editTextSpan.iEndIndex = index + 1;
                                }
                            }
                            else if (spaceCount > 1)
                            {
                                // More than one space after comma, replace
                                // with a single space.
                                editTextSpan.iEndIndex = spaceIndex;
                            }
                            else
                            {
                                // Single space after a comma and not at end
                                // of the line, leave it alone.
                                fDoEdit = false;
                            }
                            if (fDoEdit)
                            {
                                // Add edit operation
                                mgr.Add(new EditSpan(editTextSpan, replacementText));
                            }
                            index = spaceIndex;
                        }
                    }
                    startIndex = 0; // All subsequent lines start at 0
                }
                // Apply all edits
                mgr.ApplyEdits();
            }
        }
    }
}
```

## <a name="using-the-compoundaction-class"></a>CompoundAction 클래스 사용

모든는 다시 포맷 코드 섹션에서 수행 하는 단일 작업으로 되돌릴 수 여야 합니다. 사용 하 여 수행할 수 있습니다는 <xref:Microsoft.VisualStudio.Package.CompoundAction> 클래스입니다. 이 클래스는 단일 편집 작업으로 텍스트 버퍼에 대 한 편집 작업의 집합을 래핑합니다.

### <a name="example"></a>예제

사용 하는 방법의 예로 <xref:Microsoft.VisualStudio.Package.CompoundAction> 클래스입니다. 이 항목의 예제에서 "구현 지원에 대 한 서식 지정" 섹션의 예제를 참조 합니다 `DoFormatting` 메서드.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override void ReformatSpan(EditArray mgr, TextSpan span)
        {
            string description = "Reformat code";
            CompoundAction ca = new CompoundAction(this, description);
            using (ca)
            {
                ca.FlushEditActions();      // Flush any pending edits
                DoFormatting(mgr, span);    // Format the span
            }
        }
    }
}
```

## <a name="see-also"></a>관련 항목

- [레거시 언어 서비스 기능](legacy-language-service-features1.md)