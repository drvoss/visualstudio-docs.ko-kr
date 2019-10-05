---
title: 'CA1402: COM 노출 인터페이스에서 오버 로드 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: abf6382dfba8b8d9c3cc0ed6ccf90e929afca589
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694971"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: COM 노출 인터페이스에서 오버로드를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 오버 로드 된 메서드는 구성 요소 개체 모델 (COM) 표시 되는 인터페이스를 선언 합니다.

## <a name="rule-description"></a>규칙 설명
 오버로드된 메서드가 COM 클라이언트에 노출되면 첫 번째 메서드 오버로드만 이름이 유지됩니다. 이후의 오버 로드는 밑줄 문자 '_' 및 오버 로드 선언 순서에 해당 하는 정수 이름에 추가 되어 고유한 이름이 지정 됩니다. 예를 들어 다음 메서드를 것이 좋습니다.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 이러한 메서드는 다음과 같이 COM 클라이언트에 노출 됩니다.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 Visual Basic 6 COM 클라이언트는 이름에 밑줄을 사용 하 여 인터페이스 메서드를 구현할 수 없습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 고유한 이름이 되도록 오버 로드 된 메서드를 이름을 바꿉니다. 또는 숨기기 인터페이스를 COM에 대 한 접근성을 변경 하 여 `internal` (`Friend` 에 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 또는 적용 하 여 합니다 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 특성이로 설정 `false`합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 인터페이스와 규칙을 충족 하는 인터페이스를 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1413: COM 노출 값 형식에 public이 아닌 필드를 방지 합니다.](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: COM 노출 형식에 정적 멤버를 방지 합니다.](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: ComVisibleAttribute로 어셈블리 표시](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>참고 항목
 [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [Long 데이터 형식](https://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)
