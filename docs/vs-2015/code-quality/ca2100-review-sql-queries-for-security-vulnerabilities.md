---
title: 'CA2100: 보안 취약점에 대 한 SQL 쿼리를 검토 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Review SQL queries for security vulnerabilities
- ReviewSqlQueriesForSecurityVulnerabilities
- CA2100
helpviewer_keywords:
- CA2100
- ReviewSqlQueriesForSecurityVulnerabilities
ms.assetid: 79670604-c02a-448d-9c0e-7ea0120bc5fe
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 75a95e5972b26632a1cfbfce1242e49c38c9e27b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683030"
---
# <a name="ca2100-review-sql-queries-for-security-vulnerabilities"></a>CA2100: 보안상 취약한 부분이 있는지 SQL 쿼리를 검토하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewSqlQueriesForSecurityVulnerabilities|
|CheckId|CA2100|
|범주|Microsoft.Security|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 설정 하는 메서드는 <xref:System.Data.IDbCommand.CommandText%2A?displayProperty=fullName> 메서드에 문자열 인수 로부터 기본 제공 되는 문자열을 사용 하 여 속성입니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙에서는 문자열 인수에 사용자 입력이 포함된 것으로 가정합니다. 사용자 입력으로부터 만들어진 SQL 명령 문자열은 SQL 삽입 공격에 취약합니다. SQL 삽입 공격, 악의적인 사용자는 기본 데이터베이스에 무단으로 액세스 하거나 손상 하려고 쿼리 디자인을 변경 하는 입력을 제공 합니다. 일반적인 기술에 따옴표 또는 아포스트로피 SQL 리터럴 문자열 구분; 주입 포함 됩니다. SQL 주석; 의미 하는 두 개의 대시 및 새 명령을 따르는지 여부를 나타내는 세미콜론을 추가 합니다. 사용자 입력에는 쿼리를 다음 중 하나를 사용의 일부 여야 하는 경우의 공격 위험을 줄이기 위해 효율성을 순서 대로 나열 합니다.

- 저장된 프로시저를 사용 합니다.

- 매개 변수가 있는 명령 문자열을 사용 합니다.

- 명령 문자열을 만들기 전에 형식과 콘텐츠 모두에 대 한 사용자 입력의 유효성을 검사 합니다.

  다음 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 형식을 구현 합니다 <xref:System.Data.IDbCommand.CommandText%2A> 속성 또는 문자열 인수를 사용 하 여 속성을 설정 하는 생성자를 제공 합니다.

- <xref:System.Data.Odbc.OdbcCommand?displayProperty=fullName> 및 <xref:System.Data.Odbc.OdbcDataAdapter?displayProperty=fullName>

- <xref:System.Data.OleDb.OleDbCommand?displayProperty=fullName> 및 <xref:System.Data.OleDb.OleDbDataAdapter?displayProperty=fullName>

- <xref:System.Data.OracleClient.OracleCommand?displayProperty=fullName> 및 <xref:System.Data.OracleClient.OracleDataAdapter?displayProperty=fullName>

- [System.Data.SqlServerCe.SqlCeCommand](<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeCommand?qualifyHint=False&amp;autoUpgrade=True>  -->) 및 [System.Data.SqlServerCe.SqlCeDataAdapter] (<!-- TODO: review code entity reference <xref:assetId:///System.Data.SqlServerCe.SqlCeDataAdapter?qualifyHint=False&amp;autoUpgrade=True>  -->)

- <xref:System.Data.SqlClient.SqlCommand?displayProperty=fullName> 및 <xref:System.Data.SqlClient.SqlDataAdapter?displayProperty=fullName>

  형식의 ToString 메서드는 명시적 또는 암시적으로 사용 될 때이 규칙은 위반 했음을 알 수 있습니다. 쿼리 문자열을 생성 합니다. 다음은 예제입니다.

```
int x = 10;
string query = "SELECT TOP " + x.ToString() + " FROM Table";
```

 악의적인 사용자 tostring () 메서드를 재정의할 수 있으므로 규칙을 위반 합니다.

 또한 규칙 ToString 암시적으로 사용 되는 경우에 위반 됩니다.

```
int x = 10;
string query = String.Format("SELECT TOP {0} FROM Table", x);
```

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 매개 변수가 있는 쿼리를 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 명령 텍스트에 사용자 입력이 없는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 메서드를 보여 줍니다 `UnsafeQuery`에서 규칙을 위반 하는 메서드는 `SaferQuery`, 매개 변수가 있는 명령 문자열을 사용 하 여 규칙을 충족 하는 합니다.

 [!code-cpp[FxCop.Security.ReviewSqlQueries#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cpp/FxCop.Security.ReviewSqlQueries.cpp#1)]
 [!code-csharp[FxCop.Security.ReviewSqlQueries#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/cs/FxCop.Security.ReviewSqlQueries.cs#1)]
 [!code-vb[FxCop.Security.ReviewSqlQueries#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.ReviewSqlQueries/vb/FxCop.Security.ReviewSqlQueries.vb#1)]

## <a name="see-also"></a>참고 항목
 [보안 개요](https://msdn.microsoft.com/library/33e09965-61d5-48cc-9e8c-3b047cc4f194)
