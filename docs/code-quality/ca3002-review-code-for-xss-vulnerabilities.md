---
title: 'CA3002: 코드에서 XSS 취약점에 대해 검토합니다.'
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
ms.openlocfilehash: 6bcf32401abdeae499097bc5187d11154e7dfc6e
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237412"
---
# <a name="ca3002-review-code-for-xss-vulnerabilities"></a>CA3002: 코드에서 XSS 취약점에 대해 검토합니다.

|||
|-|-|
|TypeName|ReviewCodeForXssVulnerabilities|
|CheckId|CA3002|
|범주|Microsoft.Security|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

잠재적으로 신뢰할 수 없는 HTTP 요청 입력이 원시 HTML 출력에 도달 합니다.

## <a name="rule-description"></a>규칙 설명

웹 요청에서 신뢰할 수 없는 입력으로 작업할 때는 XSS (사이트 간 스크립팅) 공격에 주의 해야 합니다. XSS 공격은 신뢰할 수 없는 입력을 원시 HTML 출력에 삽입 하 여 공격자가 악의적인 스크립트를 실행 하거나 웹 페이지의 콘텐츠를 악의적으로 수정할 수 있도록 합니다. 일반적인 방법은 입력에서 악의적인 `<script>` 코드를 사용 하 여 요소를 배치 하는 것입니다. 자세한 내용은 [OWASP의 XSS](https://www.owasp.org/index.php/Cross-site_Scripting_(XSS))를 참조 하세요.

이 규칙은 원시 HTML 출력에 도달 하는 HTTP 요청에서 입력을 찾으려고 시도 합니다.

> [!NOTE]
> 이 규칙은 어셈블리 간에 데이터를 추적할 수 없습니다. 예를 들어 한 어셈블리가 HTTP 요청 입력을 읽은 다음 원시 HTML을 출력 하는 다른 어셈블리에 전달 하는 경우이 규칙은 경고를 생성 하지 않습니다.

> [!NOTE]
> 이 규칙에서 메서드 호출을 통해 데이터 흐름을 분석 하는 데 구성 가능한 제한이 있습니다. EditorConfig 파일에서 제한을 구성 하는 방법에 대 한 [Analyzer 구성](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) 을 참조 하세요.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

- 원시 HTML을 출력 하는 대신 입력을 먼저 HTML로 인코딩하는 메서드나 속성을 사용 합니다.
- 원시 HTML을 출력 하기 전에 신뢰할 수 없는 데이터를 HTML로 인코딩합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

다음 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.
- HTML을 포함 하지 않는 알려진 안전한 문자 집합에 대해 입력의 유효성을 검사 하는 것을 알고 있습니다.
- 데이터는이 규칙에 의해 검색 되지 않는 방식으로 HTML로 인코딩됩니다.

> [!NOTE]
> 이 규칙은 입력을 HTML로 인코딩하는 일부 메서드나 속성에 대해 가양성을 보고할 수 있습니다.

## <a name="pseudo-code-examples"></a>의사 코드 예제

### <a name="violation"></a>위반

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];
        Response.Write("<HTML>" + input + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")
        Me.Response.Write("<HTML>" + input + "</HTML>")
    End Sub
End Class
```

### <a name="solution"></a>솔루션

```csharp
using System;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string input = Request.Form["in"];

        // Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Response.Write("<HTML>" + Server.HtmlEncode(input) + "</HTML>");
    }
}
```

```vb
Imports System

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim input As String = Me.Request.Form("in")

        ' Example usage of System.Web.HttpServerUtility.HtmlEncode().
        Me.Response.Write("<HTML>" + Me.Server.HtmlEncode(input) + "</HTML>")
    End Sub
End Class
```