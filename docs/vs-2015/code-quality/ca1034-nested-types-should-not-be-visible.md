---
title: 'CA1034: 중첩된 형식은 표시 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
helpviewer_keywords:
- NestedTypesShouldNotBeVisible
- CA1034
ms.assetid: e9789a2c-2540-42a1-8705-ae7104011194
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 915b5807f7b14269acf4b7509ffceaecfb13af47
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62536401"
---
# <a name="ca1034-nested-types-should-not-be-visible"></a>CA1034: 중첩 형식은 노출되면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NestedTypesShouldNotBeVisible|
|CheckId|CA1034|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 외부에서 볼 수 있는 형식이 외부적으로 노출 되는 형식 선언을 포함합니다. 중첩 된 열거형 및 보호 된 형식에는이 규칙에서 제외 됩니다.

## <a name="rule-description"></a>규칙 설명
 중첩 된 형식에는 다른 형식의 범위 내에 선언 된 형식이입니다. 중첩된 형식은 포함 하는 형식의 private 구현 정보를 캡슐화 하는 데 유용 합니다. 이 용도로 사용할 경우 중첩 형식은 외부에 노출되면 안 됩니다.

 논리적 그룹에 대 한 또는; 이름 충돌을 방지 하려면 외부에서 표시 되는 중첩된 형식을 사용 하지 마십시오 대신, 네임 스페이스를 사용 합니다.

 중첩된 형식은 일부 프로그래머에 게 명확 하 게 이해 하지는 멤버 액세스 가능성의 개념을 포함 합니다.

 Protected 형식은 하위 클래스와 고급 사용자 지정 시나리오에서 중첩 된 형식에 사용할 수 있습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 중첩된 형식 외부에 노출 하지 않으려는 경우 형식의 액세스 가능성을 변경 합니다. 이 고, 그렇지 부모에서 중첩된 형식의 제거 합니다. 중첩의 용도 중첩된 형식을 분류 하려면 계층 구조를 대신 만들려는 네임 스페이스를 사용 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="example"></a>예제
 다음 예제에서는 규칙을 위반 하는 형식을 보여 줍니다.

 [!code-cpp[FxCop.Design.NestedTypes#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cpp/FxCop.Design.NestedTypes.cpp#1)]
 [!code-csharp[FxCop.Design.NestedTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/cs/FxCop.Design.NestedTypes.cs#1)]
 [!code-vb[FxCop.Design.NestedTypes#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NestedTypes/vb/FxCop.Design.NestedTypes.vb#1)]
