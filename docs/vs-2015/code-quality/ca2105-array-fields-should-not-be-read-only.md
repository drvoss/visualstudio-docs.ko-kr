---
title: 'CA2105: 배열 필드는 읽기 전용 이면 안 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4741b30d1429a1a179328c8fb4b150fc4f920612
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154382"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: 배열 필드는 읽기 전용이면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 배열을 포함 하는 public 또는 protected 필드는 읽기 전용으로 선언 됩니다.

## <a name="rule-description"></a>규칙 설명
 적용 하는 경우는 `readonly` (`ReadOnly` 에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 한정자 배열 필드를 포함 하는 필드를 다른 배열로 참조를 변경할 수 없습니다. 그러나 읽기 전용 필드에 저장된 배열의 요소는 변경할 수 있습니다. 의사 결정 또는 공개적으로 액세스할 수 있는 읽기 전용 배열 요소를 기반으로 하는 작업을 수행 하는 코드를 악용할 수 있는 보안 취약점을 포함할 수 있습니다.

 참고는 디자인 규칙을 위반 하도 공용 필드 [CA1051: 표시 되는 인스턴스 필드를 선언 하지 마십시오](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙에 의해 식별 되는 보안 취약점을 해결 하려면 자제 내용의 공개적으로 액세스할 수 있는 읽기 전용 배열입니다. 다음 절차 중 하나를 사용 하는 것이 좋습니다.

- 변경할 수 없는 강력한 형식의 컬렉션을 사용 하 여 배열을 대체 합니다. 자세한 내용은 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>을 참조하세요.

- Public 필드를 private 배열의 복제본을 반환 하는 메서드로 대체 합니다. 코드 복제본에 의존 하지 않습니다, 이므로 위험이 없는 요소를 수정할 경우.

  두 번째 방법은 했다면 바꾸지 마세요 필드 속성을 사용 하 여 부정적인 배열을 반환 하는 속성에는 성능에 영향을 합니다. 자세한 내용은 참조 하세요. [CA1819: 속성은 배열을 반환 해서는](../code-quality/ca1819-properties-should-not-return-arrays.md)합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 제외 것이 좋습니다. 거의 없는 시나리오는 읽기 전용 필드의 내용을 중요 하지 않은 발생 합니다. 이 시나리오를 사용 하 여이 경우 제거를 `readonly` 메시지를 제외 하는 대신 한정자입니다.

## <a name="example"></a>예제
 이 예제에서는이 규칙을 위반의 위험을 보여 줍니다. 첫 번째 부분에는 형식이 있는 예제 라이브러리를 보여 줍니다 `MyClassWithReadOnlyArrayField`, 두 개의 필드를 포함 하는 (`grades` 및 `privateGrades`) 보호 되지 않습니다. 필드 `grades` 공용 이며 따라서 모든 호출자에 게 취약 합니다. 필드 `privateGrades` 개인 이지만 호출자에 게 반환 되기 때문에 여전히 취약 합니다 `GetPrivateGrades` 메서드. 합니다 `securePrivateGrades` 필드에서 안전한 방식으로 노출 되는 `GetSecurePrivateGrades` 메서드. 좋은 디자인 사례를 따르는 private으로 선언 됩니다. 두 번째 부분에 저장 된 값을 변경 하는 코드를 표시 합니다 `grades` 및 `privateGrades` 멤버입니다.

 예제 클래스 라이브러리는 다음 예제에 표시 됩니다.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>예제
 다음 코드는 읽기 전용 배열 보안 문제를 설명 하기 위해 예제 클래스 라이브러리를 사용 합니다.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 이 예제에서 출력이 됩니다.

 **변조 하기 전에: 등급: 90, 90, 90 개인 등급: 90, 90, 90 보안 등급, 90, 90, 90**
**무단 변경 후: 등급: 90, 555, 90 개인 등급: 555 90, 90 등급, 90, 90, 90 보호**
## <a name="see-also"></a>참고 항목
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
