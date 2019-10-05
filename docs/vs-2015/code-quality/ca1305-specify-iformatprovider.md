---
title: 'CA1305: IFormatProvider를 지정 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 93bf7f17f77008ce8e9898c1871926edf2e8439f
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694779"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider를 지정하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|범주|Microsoft.Globalization|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 메서드 또는 생성자를 받아들이는 오버 로드가 있는 하나 이상의 멤버를 호출을 <xref:System.IFormatProvider?displayProperty=fullName> 매개 변수 및 메서드 또는 생성자는 오버 로드를 호출 하지 않습니다는 <xref:System.IFormatProvider> 매개 변수입니다. 이 규칙에 대 한 호출을 무시 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 무시로 나와 있는 메서드는 <xref:System.IFormatProvider> 매개 변수 및 또한 다음 메서드:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>규칙 설명
 경우는 <xref:System.Globalization.CultureInfo?displayProperty=fullName> 또는 <xref:System.IFormatProvider> 개체가 제공 되지 않으면, 오버 로드 된 멤버에서 제공 하는 기본 값이 모든 로캘에서 원하는 효과 없을 수 있습니다. 또한 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 멤버 기본 culture를 선택 하 고 코드에 대해 올바르지 않을 수 있다는 가정 하에 따라 서식 지정 합니다. 코드를 시나리오에 대 한 예상 대로 작동 하는지 확인 하려면 다음 지침에 따라 문화권별 형식 정보를 제공 해야 합니다.

- 사용자에 게 표시할 값을 현재 문화권을 사용 합니다. <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>을 참조하세요.

- 값을 저장 하 고 (파일이 나 데이터베이스에 유지) 소프트웨어 액세스, 하는 경우 고정 문화권을 사용 합니다. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>을 참조하세요.

- 값의 대상을 알 수 없는, 데이터 소비자 했거나 공급자 문화권을 지정 합니다.

  사실은 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> 의 인스턴스를 사용 하 여 지역화 된 리소스를 검색할 때에 사용 되며는 <xref:System.Resources.ResourceManager?displayProperty=fullName> 클래스.

  오버 로드 된 멤버의 기본 동작에 맞게 적절 한 인 경우에 코드 자체 문서화 되 고 더 쉽게 유지 관리 되도록 문화권별 오버 로드를 명시적으로 호출 하는 것이 좋습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하는 오버 로드를 사용 하 여는 <xref:System.Globalization.CultureInfo> 또는 <xref:System.IFormatProvider> 하며 이전에 나열 된 지침에 따라 인수를 지정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 기본 문화권/형식 공급자가 올바른 선택 및 코드 관리 용이성 자체가 우선 순위를 중요 한 개발 하지는 것이 확실 한 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예에서 `BadMethod` 이 규칙을 두 번 위반 합니다. `GoodMethod` 고정 문화권을 전달 하 여 첫 번째 위반을 수정 <xref:System.String.Compare%2A>, 하 고 현재 문화권을 전달 하 여 두 번째 위반 수정 <xref:System.String.ToLower%2A> 있으므로 `string3` 사용자에 게 표시 됩니다.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>예제
 다음 예제에서는 기본 현재 문화권의 결과 보여 줍니다 <xref:System.IFormatProvider> 으로 선택 되어 있는 <xref:System.DateTime> 형식입니다.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **1900 년 6 월 4 일 오후 12시 15분: 12**
**06/04/1900 12시 15분: 12**
## <a name="related-rules"></a>관련된 규칙
 [CA1304: CultureInfo를 지정 합니다.](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>참고 항목
 [NIB: CultureInfo 클래스를 사용 하 여](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
