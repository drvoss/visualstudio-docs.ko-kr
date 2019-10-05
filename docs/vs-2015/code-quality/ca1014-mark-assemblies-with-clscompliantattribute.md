---
title: 'CA1014: CLSCompliantAttribute로 어셈블리 표시 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 324f52eaac86a6ff48b71a98714b866dfca8b239
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704258"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: CLSCompliantAttribute로 어셈블리를 표시하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|범주|Microsoft.Design|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 어셈블리에 없는 <xref:System.CLSCompliantAttribute?displayProperty=fullName> 특성이 적용 합니다.

## <a name="rule-description"></a>규칙 설명
 CLS(공용 언어 사양)는 어셈블리가 여러 프로그래밍 언어에 사용될 경우 준수해야 하는 명명 제한, 데이터 형식 및 규칙을 정의합니다. 모든 어셈블리와 CLS 규격을 명시적으로 나타내기 위해 것이 좋습니다 <xref:System.CLSCompliantAttribute>합니다. 특성이 어셈블리에 없는 경우에 어셈블리는 규격이 아닙니다.

 CLS 규격 어셈블리의 형식을 포함 하거나 호환 되지 않는 멤버를 입력 하는 것이 가능 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 어셈블리에 특성을 추가 합니다. 비규격으로 전체 어셈블리를 표시 하는 대신 준수 하지 않는 및 이들이 요소 표시는 형식 또는 형식 멤버를 결정 해야 합니다. 가능한 경우 많은 어셈블리의 모든 기능에 액세스할 수 있도록 비규격 멤버를 CLS 규격 대체 항목을 제공 해야 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 어셈블리를 준수 하지 않으려면 특성을 적용 하 고 해당 값을 설정 `false`합니다.

## <a name="example"></a>예제
 다음 예제에서는 있는 어셈블리는 <xref:System.CLSCompliantAttribute?displayProperty=fullName> CLS 규격 선언 하는 특성이 적용 합니다.

 [!code-cpp[FxCop.Design.AssembliesCls#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cpp/FxCop.Design.AssembliesCls.cpp#1)]
 [!code-csharp[FxCop.Design.AssembliesCls#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/cs/FxCop.Design.AssembliesCls.cs#1)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AssembliesCls/vb/FxCop.Design.AssembliesCls.vb#1)]

## <a name="see-also"></a>참고 항목
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [언어 독립성 및 언어 독립적 구성 요소](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)
