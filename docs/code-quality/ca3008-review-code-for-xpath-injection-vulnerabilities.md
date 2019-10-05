---
title: 'CA3008: 코드에서 XPath 삽입 취약성에 대해 검토합니다.'
ms.date: 04/03/2019
ms.topic: reference
author: dotpaul
ms.author: paulming
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1d001dc306bbb225c4ecc1c0f17bf46619e2d0a7
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237256"
---
# <a name="ca3008-review-code-for-xpath-injection-vulnerabilities"></a>CA3008: 코드에서 XPath 삽입 취약성에 대해 검토합니다.

|||
|-|-|
|TypeName|ReviewCodeForXPathInjectionVulnerabilities|
|CheckId|CA3008|
|범주|Microsoft.Security|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

잠재적으로 신뢰할 수 없는 HTTP 요청 입력은 XPath 쿼리에 도달 합니다.

## <a name="rule-description"></a>규칙 설명

신뢰할 수 없는 입력으로 작업할 때는 XPath 삽입 공격에 유의 해야 합니다. 신뢰할 수 없는 입력을 사용 하 여 XPath 쿼리를 생성 하면 공격자가 쿼리를 악의적으로 조작 하 여 의도 하지 않은 결과를 반환 하 고 쿼리 된 XML의 콘텐츠를 공개할 수 있습니다.

이 규칙은 XPath 식에 도달 하는 HTTP 요청에서 입력을 찾으려고 시도 합니다.

> [!NOTE]
> 이 규칙은 어셈블리 간에 데이터를 추적할 수 없습니다. 예를 들어 한 어셈블리가 HTTP 요청 입력을 읽은 다음 XPath 쿼리를 수행 하는 다른 어셈블리에 전달 하는 경우이 규칙은 경고를 생성 하지 않습니다.

> [!NOTE]
> 이 규칙에서 메서드 호출을 통해 데이터 흐름을 분석 하는 데 구성 가능한 제한이 있습니다. EditorConfig 파일에서 제한을 구성 하는 방법에 대 한 [Analyzer 구성](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) 을 참조 하세요.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

XPath 삽입 취약점을 해결 하는 몇 가지 방법은 다음과 같습니다.

- 사용자 입력에서 XPath 쿼리를 생성 하지 않습니다.
- 입력에 안전한 문자 집합만 포함 되어 있는지 확인 합니다.
- 이스케이프 따옴표.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

안전 하 게 입력 된 입력의 유효성을 확인 한 경우이 경고를 표시 하지 않아도 됩니다.

## <a name="pseudo-code-examples"></a>의사 코드 예제

### <a name="violation"></a>위반

```csharp
using System;
using System.Xml.XPath;

public partial class WebForm : System.Web.UI.Page
{
    public XPathNavigator AuthorizedOperations { get; set; }

    protected void Page_Load(object sender, EventArgs e)
    {
        string operation = Request.Form["operation"];

        // If an attacker uses this for input:
        //     ' or 'a' = 'a
        // Then the XPath query will be:
        //     authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        // and it will return any authorizedOperation node.
        XPathNavigator node = AuthorizedOperations.SelectSingleNode(
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']");
    }
}
```

```vb
Imports System
Imports System.Xml.XPath

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Public Property AuthorizedOperations As XPathNavigator

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim operation As String = Me.Request.Form("operation")

        ' If an attacker uses this for input:
        '     ' or 'a' = 'a
        ' Then the XPath query will be:
        '      authorizedOperation[@username = 'anonymous' and @operationName = '' or 'a' = 'a']
        ' and it will return any authorizedOperation node.
        Dim node As XPathNavigator = AuthorizedOperations.SelectSingleNode( _
            "//authorizedOperation[@username = 'anonymous' and @operationName = '" + operation + "']")
    End Sub
End Class
```
