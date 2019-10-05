---
title: 레거시 언어 서비스에서 사용자 지정 문서 속성 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8422e35e5241cf1cef30d0ba4a1fe7815323d091
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312899"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>레거시 언어 서비스의 사용자 지정 문서 속성
문서 속성에 표시 될 수는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **속성** 창입니다. 프로그래밍 언어 개별 원본 파일과 연결 된 속성이 없는 일반적으로 합니다. 그러나 XML 인코딩, 스키마 및 스타일 시트에 영향을 주는 문서 속성을 지원 합니다.

## <a name="discussion"></a>토론
 언어 사용자 지정 문서 속성에서 필요한 경우에서 클래스를 파생 해야 하는 <xref:Microsoft.VisualStudio.Package.DocumentProperties> 클래스 및 파생된 클래스에서 필요한 속성을 구현 합니다.

 또한 문서 속성은 일반적으로 원본 파일 자체에 저장 됩니다. 이렇게 하려면 표시할 소스 파일에서 속성 정보를 구문 분석할 수 있도록 언어 서비스를 **속성** 창 및 문서 속성에 변경 될 때 원본 파일을 업데이트 하는  **속성** 창입니다.

## <a name="customize-the-documentproperties-class"></a>DocumentProperties 클래스를 사용자 지정
 를 지원 하기 위해 사용자 지정 문서 속성에서 클래스를 파생 해야 하는 <xref:Microsoft.VisualStudio.Package.DocumentProperties> 클래스 및 필요에 따라 많은 속성을 추가 합니다. 사용자 특성 구성에 제공 해야 합니다 **속성** 창 표시 합니다. 속성에만 있는 경우는 `get` 접근자에서 읽기 전용으로 표시 됩니다는 **속성** 창. 속성 둘 다 있으면 `get` 하 고 `set` 접근자 속성을 업데이트할 수도 있습니다에 **속성** 창입니다.

### <a name="example"></a>예제
 파생 된 클래스 예제는 다음과 같습니다 <xref:Microsoft.VisualStudio.Package.DocumentProperties>, 두 속성을 보여 주는 `Filename` 고 `Description`입니다. 속성이 업데이트 되는 경우, 사용자 지정 메서드를는 <xref:Microsoft.VisualStudio.Package.LanguageService> 속성 소스 파일에 쓸 클래스 라고 합니다.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestDocumentProperties : DocumentProperties
    {
        private string m_filename;
        private string m_description;

        public TestDocumentProperties(CodeWindowManager mgr)
            : base(mgr)
        {
        }

        // Helper function to initialize this property without
        // going through the FileName property (which does a lot
        // more than we need when the filename is set).
        public void SetFileName(string filename)
        {
            m_filename = filename;
        }

        // Helper function to initialize this property without
        // going through the Description property (which does a lot
        // more than we need when the description is set).
        public void SetDescription(string description)
        {
            m_description = description;
        }

        ////////////////////////////////////////////////////////////
        // The document properties

        [CategoryAttribute("General")]
        [DescriptionAttribute("Name of the file")]
        [DisplayNameAttribute("Filename")]
        public string FileName
        {
            get { return m_filename; }
            set
            {
               if (value != m_filename)
               {
                    m_filename = value;
                    SetPropertyValue("Filename", m_filename);
               }
            }
        }

        [CategoryAttribute("General")]
        [DescriptionAttribute("Description of the file")]
        [DisplayNameAttribute("Description")]
        public string Description
        {
            get { return m_description; }
            set
            {
                if (value != m_description)
                {
                    m_description = value;
                    SetPropertyValue("Description", m_description);
                }
            }
        }

        ///////////////////////////////////////////////////////////
        // Private methods.

        private void SetPropertyValue(string propertyName, string propertyValue)
        {
            Source src = this.GetSource();
            if (src != null)
            {
                TestLanguageService service = src.LanguageService as TestLanguageService;
                if (service != null)
                {
                    // Set the property in to the source file.
                    service.SetPropertyValue(src, propertyName, propertyValue);
                }
            }
        }
    }
}
```

## <a name="instantiate-the-custom-documentproperties-class"></a>사용자 지정 DocumentProperties 클래스 인스턴스화
 사용자 지정 문서 속성 클래스를 인스턴스화할 때 재정의 해야 합니다는 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> 사용 중인 버전에서 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService> 의 단일 인스턴스를 반환 하는 클래스에 <xref:Microsoft.VisualStudio.Package.DocumentProperties> 클래스입니다.

### <a name="example"></a>예제

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        private TestDocumentProperties m_documentProperties;

        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)
        {
            if (m_documentProperties == null)
            {
                m_documentProperties = new TestDocumentProperties(mgr);
            }
            return m_documentProperties;
        }
    }
}
```

## <a name="properties-in-the-source-file"></a>소스 파일의 속성
 문서 속성에 일반적으로 소스 파일에 특정 되므로 값은 원본 파일 자체에 저장 됩니다. 이렇게 하려면 언어 파서 또는 스캐너 이러한 속성을 정의를 지원 합니다. 예를 들어, XML 문서 속성은 루트 노드에 저장 됩니다. 경우 루트 노드에서 값을 수정 합니다 **속성** 창 값이 변경 되 고 편집기에서 루트 노드 업데이트 됩니다.

### <a name="example"></a>예제
 속성을 저장 하는이 예제 `Filename` 고 `Description` 소스 파일의 처음 두 줄에 포함 된 특수 주석 헤더에으로:

```
//!Filename = file.testext
//!Description = A sample file
```

 이 예제에서는 가져오기 및 사용자 소스 파일을 직접 수정 하는 경우 속성은 업데이트 방법과 소스 파일의 처음 두 줄에서 문서 속성을 설정 하는 데 필요한 두 메서드를 보여 줍니다. `SetPropertyValue` 같습니다. 동일한 예에서 하나에서 메서드를 호출할 합니다 `TestDocumentProperties` 에 표시 된 대로 클래스를 *DocumentProperties 클래스 사용자 지정* 섹션.

 이 예제에서는 처음 두 줄에서 토큰의 형식을 결정 하려면 스캐너를 사용 합니다. 이 예제는 설명 목적 으로만 제공 됩니다. 이 상황을 좀 더 일반적인 방법은 무엇 이라고 구문 분석 트리 트리의 각 노드는 특정 토큰에 대 한 정보를 포함 하는 위치를 소스 파일을 구문 분석 하는 것입니다. 루트 노드는 문서 속성을 포함 됩니다.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    // TokenType.Comment is the last item in that enumeration.
    public enum TestTokenTypes
    {
        DocPropertyLine = TokenType.Comment + 1,
        DocPropertyName,
        DocPropertyAssign,
        DocPropertyValue
    }

    class TestLanguageService : LanguageService
    {
        // Search this many lines from the beginning for properties.
        private static int maxLinesToSearch = 2;

        private TestDocumentProperties m_documentProperties;

        // Called whenever a full parsing operation has completed.
        public override void OnParseComplete(ParseRequest req)
        {
            if (m_documentProperties != null)
            {
                Source src = GetSource(req.View);
                if (src != null)
                {
                    string value = GetPropertyValue(src, "Filename");
                    m_documentProperties.SetFileName(value);

                    value = GetPropertyValue(src, "Description");
                    m_documentProperties.SetDescription(value);

                    // Update the Properties Window.
                    m_documentProperties.Refresh();
                }
            }
        }

        // Retrieves the specified property value from the given source.
        public string GetPropertyValue(Source src, string propertyName)
        {
            string propertyValue = "";

            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    string      line;
                    TokenInfo[] lineInfo = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line.
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                for ( ;
                                     tokenIndex < lineInfo.Length;
                                     tokenIndex++)
                                {
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)
                                    {
                                        break;
                                    }
                                }
                                if (tokenIndex < lineInfo.Length)
                                {
                                    propertyValue = src.GetText(i,
                                                          lineInfo[tokenIndex].StartIndex,
                                                          i,
                                                          lineInfo[tokenIndex].EndIndex + 1);
                                }
                                break;
                            }
                        }
                    }
                }
            }
            return propertyValue;
        }

        // Sets the specified property into the given source file.
        // Called from the TestDocumentProperties class.
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)
        {
            string newLine;

            if (propertyName == null || propertyName == "")
            {
                // No property name, so nothing to do
                return;
            }
            if (propertyValue == null)
            {
                propertyValue = "";
            }
            // This is the line to be inserted.
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);

            // First, find the line on which the property belongs.
            // If line is found, replace it.
            // Otherwise, insert the line at the beginning of the file.
            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    int         lineNumber = -1;
                    string      line;
                    TokenInfo[] lineInfo   = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                lineNumber = i;
                                break;
                            }
                        }
                    }

                    // Set up an undo context that also handles the insert/replace.
                    EditArray editArray = new EditArray(src,
                                                        true,
                                                        "Update Property");
                    if (editArray != null)
                    {
                        TextSpan span = new TextSpan();
                        if (lineNumber != -1)
                        {
                            // Replace line.
                            int lineLength = 0;
                            src.GetTextLines().GetLengthOfLine(lineNumber,
                                                               out lineLength);
                            span.iStartLine  = lineNumber;
                            span.iStartIndex = 0;
                            span.iEndLine    = lineNumber;
                            span.iEndIndex   = lineLength;
                        }
                        else
                        {
                            // Insert new line.
                            span.iStartLine  = 0;
                            span.iStartIndex = 0;
                            span.iEndLine    = 0;
                            span.iEndIndex   = 0;
                            newLine += "\n";
                        }
                        editArray.Add(new EditSpan(span, newLine));
                        editArray.ApplyEdits();
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>참고자료
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)