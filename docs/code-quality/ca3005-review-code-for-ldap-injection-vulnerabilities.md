---
title: 'CA3005: 코드에서 LDAP 주입 취약점에 대해 검토합니다.'
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
ms.openlocfilehash: c0c99d5d0adb145a061693f8a83b1f674e05eed4
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237336"
---
# <a name="ca3005-review-code-for-ldap-injection-vulnerabilities"></a>CA3005: 코드에서 LDAP 주입 취약점에 대해 검토합니다.

|||
|-|-|
|TypeName|ReviewCodeForLdapInjectionVulnerabilities|
|CheckId|CA3005|
|범주|Microsoft.Security|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

잠재적으로 신뢰할 수 없는 HTTP 요청 입력은 LDAP 문에 도달 합니다.

## <a name="rule-description"></a>규칙 설명

신뢰할 수 없는 입력으로 작업 하는 경우 LDAP (Lightweight Directory Access Protocol) 삽입 공격에 유의 해야 합니다. 공격자는 잠재적으로 정보 디렉터리에 대해 악의적인 LDAP 문을 실행할 수 있습니다. 사용자 입력을 사용 하 여 디렉터리 서비스에 액세스할 수 있는 동적 LDAP 문을 생성 하는 응용 프로그램은 특히 취약 합니다.

이 규칙은 LDAP 문에 도달 하는 HTTP 요청에서 입력을 찾으려고 시도 합니다.

> [!NOTE]
> 이 규칙은 어셈블리 간에 데이터를 추적할 수 없습니다. 예를 들어 한 어셈블리가 HTTP 요청 입력을 읽은 다음 LDAP 문을 실행 하는 다른 어셈블리에 전달 하는 경우이 규칙은 경고를 생성 하지 않습니다.

> [!NOTE]
> 이 규칙에서 메서드 호출을 통해 데이터 흐름을 분석 하는 데 구성 가능한 제한이 있습니다. EditorConfig 파일에서 제한을 구성 하는 방법에 대 한 [Analyzer 구성](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) 을 참조 하세요.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

LDAP 문의 사용자 제어 부분에 대해서는 다음 중 하나를 고려 하십시오.
- 특수 문자가 아닌 문자에 대 한 안전한 목록만 허용 합니다.
- 특수 문자 허용 안 함
- 특수 문자를 이스케이프 합니다.

자세한 지침은 [OWASP의 LDAP 주입 방지 참고 자료 시트](https://github.com/OWASP/CheatSheetSeries/blob/master/cheatsheets/LDAP_Injection_Prevention_Cheat_Sheet.md) 를 참조 하세요.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

입력의 유효성을 검사 하거나 안전 하 게 이스케이프 처리 한 경우이 경고를 표시 하지 않을 수 있습니다.

## <a name="pseudo-code-examples"></a>의사 코드 예제

### <a name="violation"></a>위반

```csharp
using System;
using System.DirectoryServices;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userName = Request.Params["user"];
        string filter = "(uid=" + userName + ")";  // searching for the user entry

        // In this example, if we send the * character in the user parameter which will
        // result in the filter variable in the code to be initialized with (uid=*).
        // The resulting LDAP statement will make the server return any object that
        // contains a uid attribute.
        DirectorySearcher searcher = new DirectorySearcher(filter);
        SearchResultCollection results = searcher.FindAll();

        // Iterate through each SearchResult in the SearchResultCollection.
        foreach (SearchResult searchResult in results)
        {
            // ...
        }
    }
}
```

```vb
Imports System
Imports System.DirectoryServices

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(send As Object, e As EventArgs)
        Dim userName As String = Me.Request.Params(""user"")
        Dim filter As String = ""(uid="" + userName + "")""    ' searching for the user entry

        ' In this example, if we send the * character in the user parameter which will
        ' result in the filter variable in the code to be initialized with (uid=*).
        ' The resulting LDAP statement will make the server return any object that
        ' contains a uid attribute.
        Dim searcher As DirectorySearcher = new DirectorySearcher(filter)
        Dim results As SearchResultCollection = searcher.FindAll()

        ' Iterate through each SearchResult in the SearchResultCollection.
        For Each searchResult As SearchResult in results
            ' ...
        Next searchResult
    End Sub
End Class
```
