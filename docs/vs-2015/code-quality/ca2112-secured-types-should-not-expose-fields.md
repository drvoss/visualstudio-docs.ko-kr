---
title: 'CA2112: 보안된 형식은 필드를 노출 해야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2112
- SecuredTypesShouldNotExposeFields
helpviewer_keywords:
- SecuredTypesShouldNotExposeFields
- CA2112
ms.assetid: 9eb13a78-3487-49f2-81d1-3c3866db132f
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 17a52b952437ce136773d796972c6619a9733749
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687321"
---
# <a name="ca2112-secured-types-should-not-expose-fields"></a>CA2112: 보안 형식은 필드를 노출하면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecuredTypesShouldNotExposeFields|
|CheckId|CA2112|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 public 필드를 포함 하 고로 보호 되는 [링크 요구가](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)합니다.

## <a name="rule-description"></a>규칙 설명
 코드에 링크 요청으로 보안된 형식의 인스턴스에 대한 액세스 권한이 있으면 코드에서 링크 요청을 만족하지 않아도 해당 형식의 필드에 액세스할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 public이 아닌 필드를 확인 하 고 공용 속성 또는 필드 데이터를 반환 하는 메서드를 추가 합니다. 형식의 속성 및 메서드에 대 한 액세스를 보호 하는 형식에 LinkDemand 보안 검사. 그러나 코드 액세스 보안 필드에 적용 되지 않습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 모두 보안 문제 및 바람직한 디자인에 대 한 public이 아닌 public 필드를 만들어 위반 문제를 해결 해야 합니다. 필드는 보안을 유지 해야 하는 정보를 유지 하지 않으면이 규칙에서 경고를 무시할 수 있습니다 하 고 필드의 내용에 의존 하지 마십시오.

## <a name="example"></a>예제
 다음 예에서는 라이브러리 형식의 구성 됩니다 (`SecuredTypeWithFields`) 형식 안전 하지 않은 필드를 사용 하 여 (`Distributor`) 라이브러리 형식의 인스턴스를 만들 수 및 형식에 잘못된 전달 인스턴스를 만들 수 있는 권한이 없는 응용 프로그램 코드 인스턴스의 필드 형식을 보호 하는 권한이 없는 경우에 읽을 수 있습니다.

 다음 라이브러리 코드는 규칙을 위반합니다.

 [!code-csharp[FxCop.Security.LinkDemandOnField#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LinkDemandOnField/cs/FxCop.Security.LinkDemandOnField.cs#1)]

## <a name="example"></a>예제
 보안된 형식을 보호 하는 링크 요청으로 인해 응용 프로그램 인스턴스를 만들 수 없습니다. 다음 클래스에는 응용 프로그램을 보안 된 형식의 인스턴스를 가져올 수 있습니다.

 [!code-csharp[FxCop.Security.LDOnFieldsDistributor#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.LDOnFieldsDistributor/cs/FxCop.Security.LDOnFieldsDistributor.cs#1)]

## <a name="example"></a>예제
 다음 응용 프로그램, 보안 된 형식의 메서드에 액세스 하려면 권한이 없으면 코드 액세스 하는 방법을 해당 필드를 보여 줍니다.

 [!code-csharp[FxCop.Security.TestLinkDemandOnFields#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestLinkDemandOnFields/cs/FxCop.Security.TestLinkDemandOnFields.cs#1)]

 이 예제의 결과는 다음과 같습니다.

 **SecuredTypeWithFields의 인스턴스를 만드는 중입니다.** 
**보안 된 형식 필드: 22, 33**
**보안 된 형식의 필드를 변경 하는 중...** 
**캐시 개체 필드: 99, 33**
## <a name="related-rules"></a>관련된 규칙
 [CA1051: 표시 되는 인스턴스 필드 선언 하지 마십시오.](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)

## <a name="see-also"></a>참고 항목
 [링크 요청만](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [데이터 및 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
