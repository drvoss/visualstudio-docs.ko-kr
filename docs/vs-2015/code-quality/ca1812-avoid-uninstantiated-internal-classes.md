---
title: 'CA1812: 인스턴스화되지 않은 내부 클래스 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1812
- AvoidUninstantiatedInternalClasses
helpviewer_keywords:
- AvoidUninstantiatedInternalClasses
- CA1812
ms.assetid: 1bb92a42-322a-44cc-98a8-8858212c1e1f
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f44dcb010dd9c62d130913efd590a4c1b651de50
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157986"
---
# <a name="ca1812-avoid-uninstantiated-internal-classes"></a>CA1812: 인스턴스화되지 않은 내부 클래스를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidUninstantiatedInternalClasses|
|CheckId|CA1812|
|범주|Microsoft.Performance|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 어셈블리 수준 형식의 인스턴스가 어셈블리에서 코드에 의해 만들어지지 않습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙 형식 생성자 중 하나에 대 한 호출을 찾으려고 하 고 호출이 있으면 위반을 보고 합니다.

 이 규칙에서 다음 형식은 검사 하지 않습니다.

- 값 형식

- 추상 형식

- 열거형

- 대리자

- 컴파일러에서 내보낸 배열 형식

- 인스턴스화할 수 없습니다 및 정의 하는 형식을 `static` (`Shared` Visual Basic의) 메서드만 있습니다.

  적용 하는 경우 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute?displayProperty=fullName> 분석 되는 어셈블리에이 규칙으로 표시 되는 생성자에서 발생 하지 것입니다 `internal` 다른 필드가 사용 되 고 있는지 여부를 알 수 없습니다 때문에 `friend` 어셈블리입니다.

  이 제한을 해결할 수 있지만 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 코드 분석, 외부 독립 실행형 FxCop 경우에 발생 내부 생성자에 모든 `friend` 어셈블리는 분석에 포함 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하 고, 형식을 제거 또는 사용 하는 코드를 추가 합니다. 형식을 정적 메서드만 있으면 컴파일러가 기본 public 인스턴스 생성자를 내보내는 하지 않도록 하려면 형식에 다음 중 하나를 추가 합니다.

- 에 대 한 private 생성자를 대상으로 하는 형식 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전 1.0 및 1.1입니다.

- 합니다 `static` (`Shared` Visual basic에서) 한정자를 대상으로 하는 형식 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)]합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 표시 하지 않아도 안전 합니다. 다음과 같은 상황에서이 경고를 표시 하는 것이 좋습니다.

- 클래스가 만들어질 바인딩된 리플렉션 메서드를 통해 같은 <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>합니다.

- 클래스는 런타임 또는 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]에 의해 자동으로 만들어집니다. 이러한 예로 <xref:System.Configuration.IConfigurationSectionHandler?displayProperty=fullName> 또는 <xref:System.Web.IHttpHandler?displayProperty=fullName>를 구현하는 클래스를 들 수 있습니다.

- 클래스는 새 제약 조건이 있는 제네릭 형식 매개 변수로 전달 됩니다. 예를 들어, 다음 예제에서는이 규칙을 발생 합니다.

  ```csharp
  internal class MyClass
  {
      public DoSomething()
      {
      }
  }
  public class MyGeneric<T> where T : new()
  {
      public T Create()
      {
          return new T();
      }
  }
  // [...]
  MyGeneric<MyClass> mc = new MyGeneric<MyClass>();
  mc.Create();
  ```

  이러한 상황에서이 경고를 표시 하는 것이 좋습니다.

## <a name="related-rules"></a>관련된 규칙
 [CA1811: 호출 되지 않는 전용 코드를 방지 합니다.](../code-quality/ca1811-avoid-uncalled-private-code.md)

 [CA1801: 사용 되지 않는 매개 변수를 검토](../code-quality/ca1801-review-unused-parameters.md)

 [CA1804: 사용 되지 않는 로컬 항목을 제거](../code-quality/ca1804-remove-unused-locals.md)
