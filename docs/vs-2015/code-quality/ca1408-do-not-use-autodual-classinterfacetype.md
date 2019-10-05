---
title: 'CA1408: AutoDual ClassInterfaceType을 사용 하지 마십시오 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 88d23ee703b482813ad0a5401e9dea7adf9a063c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705701"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: AutoDual ClassInterfaceType을 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|범주|Microsoft.Interoperability|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 구성 요소 개체 모델 (COM) 표시 형식으로 표시 됩니다는 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 특성이로 설정 합니다 `AutoDual` 의 값 <xref:System.Runtime.InteropServices.ClassInterfaceType>합니다.

## <a name="rule-description"></a>규칙 설명
 이중 인터페이스를 사용하는 형식에서는 클라이언트가 특정 인터페이스 레이아웃에 바인딩할 수 있습니다. 이후 버전에서 해당 형식이나 기본 형식의 레이아웃이 변경되면 인터페이스에 바인딩된 COM 클라이언트의 바인딩이 해제될 수 있습니다. 기본적으로 하는 경우는 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 특성 지정 하지 않으면 디스패치 전용 인터페이스를 사용 합니다.

 그렇지 않은 경우에 표시 하지 않는 한 모든 공용 제네릭이 아닌 형식은 COM에 표시 되지만; 모든 public이 아닌 형식과 일반 COM에 표시 되지 않습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면의 값을 변경 합니다 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 특성을 `None` 의 값 <xref:System.Runtime.InteropServices.ClassInterfaceType> 인터페이스를 명시적으로 정의 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 특정 형식 및 해당 기본 형식 레이아웃을 이후 버전에서 변경 되지 않습니다 아닌 경우이 규칙에서 경고를 표시 하지 마십시오.

## <a name="example"></a>예제
 다음 예제에서는 명시적 인터페이스를 사용 하는 클래스를 다시 선언 규칙을 위반 하는 클래스를 보여 줍니다.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>관련된 규칙
 [CA1403: 자동 레이아웃 형식은 com 노출 이면 안](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: ComSource 인터페이스 IDispatch로 표시](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>참고 항목
 [클래스 인터페이스 소개](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [상호 운용할.NET 형식의 정규화](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [비관리 코드와의 상호 운용](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
