---
title: 'CA1305: IFormatProvider 지정 | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 299e8bfec526dc3a5e8dc166d9ab405d51037cbe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661436"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider를 지정하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|범주|Microsoft 세계화|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 메서드 또는 생성자가 <xref:System.IFormatProvider?displayProperty=fullName> 매개 변수를 허용 하는 오버 로드를 포함 하는 하나 이상의 멤버를 호출 하 고, 메서드 또는 생성자는 <xref:System.IFormatProvider> 매개 변수를 사용 하는 오버 로드를 호출 하지 않습니다. 이 규칙은 <xref:System.IFormatProvider> 매개 변수를 무시 하는 것으로 설명 된 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 메서드에 대 한 호출을 무시 하 고 다음 메서드도 추가로 설명 합니다.

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>규칙 설명
 @No__t_0 또는 <xref:System.IFormatProvider> 개체를 제공 하지 않으면 오버 로드 된 멤버에서 제공 하는 기본값이 모든 로캘에서 원하는 효과를 갖지 않을 수 있습니다. 또한 멤버 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 기본 문화권을 선택 하 고 코드에 맞지 않을 수 있는 가정을 기반으로 서식을 지정 합니다. 시나리오에 대해 코드가 예상 대로 작동 하는지 확인 하려면 다음 지침에 따라 문화권 관련 정보를 제공 해야 합니다.

- 값이 사용자에 게 표시 되 면 현재 문화권을 사용 합니다. <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>을 참조하세요.

- 파일이 나 데이터베이스에 유지 되는 소프트웨어에서 값을 저장 하 고 액세스 하는 경우 고정 문화권을 사용 합니다. <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>을 참조하세요.

- 값의 대상을 모르는 경우 데이터 소비자 또는 공급자가 문화권을 지정 하도록 합니다.

  @No__t_0은 <xref:System.Resources.ResourceManager?displayProperty=fullName> 클래스의 인스턴스를 사용 하 여 지역화 된 리소스를 검색 하는 데만 사용 됩니다.

  오버 로드 된 멤버의 기본 동작이 사용자의 요구 사항에 적합 한 경우에도 코드를 자체 문서화 하 고 더 쉽게 유지 관리할 수 있도록 문화권 관련 오버 로드를 명시적으로 호출 하는 것이 좋습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 <xref:System.Globalization.CultureInfo> 또는 <xref:System.IFormatProvider>를 사용 하는 오버 로드를 사용 하 고 앞에서 설명한 지침에 따라 인수를 지정 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 기본 culture/형식 공급자가 올바른 선택이 고 코드 유지 관리는 중요 한 개발 우선 순위가 아닌 것이 확실 한 경우이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 `BadMethod`이이 규칙의 두 위반을 발생 시킵니다. `GoodMethod`는 고정 문화권을 <xref:System.String.Compare%2A>에 전달 하 여 첫 번째 위반을 수정 하 고 `string3` 사용자에 게 표시 되기 때문에 현재 문화권을 <xref:System.String.ToLower%2A>에 전달 하 여 두 번째 위반을 수정 합니다.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>예제
 다음 예제에서는 <xref:System.DateTime> 형식에 의해 선택 되는 기본 <xref:System.IFormatProvider>에 대 한 현재 문화권의 영향을 보여 줍니다.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **오후 6/4/1900 12:15:12** 
**06/04/1900 12:15:12**
## <a name="related-rules"></a>관련 규칙
 [CA1304: CultureInfo ](../code-quality/ca1304-specify-cultureinfo.md) 지정

## <a name="see-also"></a>관련 항목:
 [NIB: CultureInfo 클래스를 사용 하 여 ](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
