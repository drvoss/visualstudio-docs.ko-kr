---
title: 'CA1407: COM 노출 형식에 정적 멤버 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
helpviewer_keywords:
- CA1407
- AvoidStaticMembersInComVisibleTypes
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 93c56c17998bbe672ed5816fc950eec5cc56b1c3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705730"
---
# <a name="ca1407-avoid-static-members-in-com-visible-types"></a>CA1407: COM 노출 형식에 정적 멤버를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidStaticMembersInComVisibleTypes|
|CheckId|CA1407|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 특히 표시 구성 요소 개체 모델 (COM)에 표시 된 형식에 포함 된 `public``static` 메서드.

## <a name="rule-description"></a>규칙 설명
 COM을 지원 하지 않습니다 `static` 메서드.

 이 규칙 무시 속성 및 이벤트 접근자, 메서드 또는 메서드 중 하나를 사용 하 여 표시 되는 오버 로드 연산자는 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName> 특성 또는 <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName> 특성입니다.

 기본적으로 다음은 COM에 표시: 어셈블리, public 형식, 공용 인스턴스 멤버를 공용 형식 및 공개 값 형식의 모든 멤버입니다.

 이 규칙을 사용 하려면 어셈블리 수준에 대 한 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 로 설정 되어야 합니다 `false` 고 클래스 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 로 변경 해야 `true`처럼 다음 코드를 보여 줍니다.

```csharp
using System;
using System.Runtime.InteropServices;

[assembly: ComVisible(false)]
namespace Samples
{
    [ComVisible(true)]
    public class MyClass
    {
        public static void DoSomething()
        {
        }
    }
}
```

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 동일한 기능을 제공 하는 인스턴스 메서드를 사용 하도록 디자인 변경 된 `static` 메서드.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 COM 클라이언트에서 제공 하는 기능에 액세스할 필요가 없는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다는 `static` 메서드.

## <a name="example-violation"></a>예제 위반

### <a name="description"></a>설명
 다음 예제와 `static` 이 규칙을 위반 하는 메서드입니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersViolation/cs/FxCop.Interoperability.ComVisibleStaticMembersViolation.cs#1)]

### <a name="comments"></a>설명
 이 예제는 **Book.FromPages** com에서 메서드를 호출할 수 없습니다

## <a name="example-fix"></a>예제 수정

### <a name="description"></a>설명
 를 이전 예제에서 위반을 해결 하려면 인스턴스 메서드를 메서드를 변경할 수 있습니다 하지만 무의미 이런에서 합니다. 더 나은 방법은 명시적으로 적용할 `ComVisible(false)` com에서 메서드를 볼 수 없는 다른 개발자에의 선택을 취소 하는 방법

 다음 예제에서는 <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> 방법입니다.

### <a name="code"></a>코드
 [!code-csharp[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.ComVisibleStaticMembersFixed/cs/FxCop.Interoperability.ComVisibleStaticMembersFixed.cs#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1017: ComVisibleAttribute로 어셈블리 표시](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

 [CA1406: Visual Basic 6 클라이언트에서 Int64 인수를 방지 합니다.](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)

 [CA1413: COM 노출 값 형식에 public이 아닌 필드를 방지 합니다.](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

## <a name="see-also"></a>참고 항목
 [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
