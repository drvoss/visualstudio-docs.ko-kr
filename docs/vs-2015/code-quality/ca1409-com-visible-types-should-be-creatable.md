---
title: 'CA1409: Com 노출 형식을 만들 수 있어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7bd52ad75c67f9c8faa80e84eb5ae09c22c25280
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65678873"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409: Com 노출 형식을 만들 수 있어야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 특히 표시 구성 요소 개체 모델 (COM)에 표시 되는 참조 형식 매개 변수가 있는 public 생성자를 포함 하지만 (매개 변수가 없는) 공용 기본 생성자가 포함 되지 않습니다.

## <a name="rule-description"></a>규칙 설명
 COM 클라이언트에서 공용 기본 생성자가 없는 형식을 만들 수 없습니다. 그러나 형식 여전히 액세스할 수 있습니다 COM 클라이언트에서 다른 방법 예를 들어 (메서드 호출의 반환 값)를 통해 클라이언트에 전달 및 형식을 만들 수 있는 경우.

 규칙에서 파생 된 형식은 무시 <xref:System.Delegate?displayProperty=fullName>합니다.

 기본적으로 다음은 COM에 표시: 어셈블리, public 형식, 공용 인스턴스 멤버를 공용 형식 및 공개 값 형식의 모든 멤버입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 공용 기본 생성자를 추가 하거나 제거 합니다 <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> 형식에서입니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 다른 방법으로 만들 COM 클라이언트에 개체를 전달 하는 제공 되는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="related-rules"></a>관련된 규칙
 [CA1017: ComVisibleAttribute로 어셈블리 표시](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>참고 항목
 [상호 운용할.NET 형식의 정규화](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
