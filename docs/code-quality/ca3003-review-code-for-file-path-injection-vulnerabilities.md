---
title: 'CA3003: 코드에서 파일 경로 삽입 취약성에 대해 검토합니다.'
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
ms.openlocfilehash: c9e43dcdf1e923cb7bc4a98b17fd0be71b7927eb
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237407"
---
# <a name="ca3003-review-code-for-file-path-injection-vulnerabilities"></a>CA3003: 코드에서 파일 경로 삽입 취약성에 대해 검토합니다.

|||
|-|-|
|TypeName|ReviewCodeForFilePathInjectionVulnerabilities|
|CheckId|CA3003|
|범주|Microsoft.Security|
|주요 변경 내용|최신이 아님|

## <a name="cause"></a>원인

잠재적으로 신뢰할 수 없는 HTTP 요청 입력은 파일 작업 경로에 도달 합니다.

## <a name="rule-description"></a>규칙 설명

웹 요청에서 신뢰할 수 없는 입력으로 작업 하는 경우 파일에 대 한 경로를 지정 하는 경우 사용자가 제어 하는 입력을 사용할 수 있습니다. 공격자는 의도 하지 않은 파일을 읽을 수 있으므로 중요 한 데이터의 정보가 공개 될 수 있습니다. 또는 공격자가 의도 하지 않은 파일에 쓸 수 있으므로 중요 한 데이터를 무단으로 수정 하거나 서버의 보안을 손상 시킬 수 있습니다. 일반적인 공격자 기술은 [경로 순회](https://www.owasp.org/index.php/Path_Traversal) 를 사용 하 여 원하는 디렉터리 외부의 파일에 액세스 합니다.

이 규칙은 파일 작업에서 경로에 도달 하는 HTTP 요청에서 입력을 찾으려고 시도 합니다.

> [!NOTE]
> 이 규칙은 어셈블리 간에 데이터를 추적할 수 없습니다. 예를 들어 한 어셈블리가 HTTP 요청 입력을 읽은 다음 파일에 쓰는 다른 어셈블리에 전달 하는 경우이 규칙은 경고를 생성 하지 않습니다.

> [!NOTE]
> 이 규칙에서 메서드 호출을 통해 데이터 흐름을 분석 하는 데 구성 가능한 제한이 있습니다. EditorConfig 파일에서 제한을 구성 하는 방법에 대 한 [Analyzer 구성](https://github.com/dotnet/roslyn-analyzers/blob/master/docs/Analyzer%20Configuration.md#dataflow-analysis) 을 참조 하세요.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

- 가능 하면 사용자 입력에 따라 파일 경로를 명시적으로 알려진 안전 목록으로 제한 합니다.  예를 들어 응용 프로그램이 "red.aspx", "red.aspx" 또는 "blue .txt"에만 액세스 해야 하는 경우 해당 값만 허용 합니다.
- 신뢰할 수 없는 파일 이름을 확인 하 고 이름이 제대로 구성 되었는지 확인 합니다.
- 경로를 지정할 때 전체 경로 이름을 사용 합니다.
- Path 환경 변수와 같은 잠재적으로 위험한 구문을 피합니다.
- 사용자가 짧은 이름을 제출 하는 경우 긴 파일 이름만 허용 하 고 긴 이름의 유효성을 검사 합니다.
- 최종 사용자 입력을 올바른 문자로 제한 합니다.
- MAX_PATH 길이를 초과 하는 이름을 거부 합니다.
- 해석 하지 않고 파일 이름을 그대로 처리 합니다.
- 파일 이름이 파일 또는 장치를 나타내는지 여부를 확인 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

이전 섹션에 설명 된 대로 입력의 유효성을 검사 한 경우이 경고를 표시 하지 않아도 됩니다.

## <a name="pseudo-code-examples"></a>의사 코드 예제

### <a name="violation"></a>위반

```csharp
using System;
using System.IO;

public partial class WebForm : System.Web.UI.Page
{
    protected void Page_Load(object sender, EventArgs e)
    {
        string userInput = Request.Params["UserInput"];
        // Assume the following directory structure:
        //   wwwroot\currentWebDirectory\user1.txt
        //   wwwroot\currentWebDirectory\user2.txt
        //   wwwroot\secret\allsecrets.txt
        // There is nothing wrong if the user inputs:
        //   user1.txt
        // However, if the user input is:
        //   ..\secret\allsecrets.txt
        // Then an attacker can now see all the secrets.

        // Avoid this:
        using (File.Open(userInput, FileMode.Open))
        {
            // Read a file with the name supplied by user
            // Input through request's query string and display
            // The content to the webpage.
        }
    }
}
```

```vb
Imports System
Imports System.IO

Partial Public Class WebForm
    Inherits System.Web.UI.Page

    Protected Sub Page_Load(sender As Object, e As EventArgs)
        Dim userInput As String = Me.Request.Params("UserInput")
        ' Assume the following directory structure:
        '   wwwroot\currentWebDirectory\user1.txt
        '   wwwroot\currentWebDirectory\user2.txt
        '   wwwroot\secret\allsecrets.txt
        ' There is nothing wrong if the user inputs:
        '   user1.txt
        ' However, if the user input is:
        '   ..\secret\allsecrets.txt
        ' Then an attacker can now see all the secrets.

        ' Avoid this:
        Using File.Open(userInput, FileMode.Open)
            ' Read a file with the name supplied by user
            ' Input through request's query string and display
            ' The content to the webpage.
        End Using
    End Sub
End Class
```
