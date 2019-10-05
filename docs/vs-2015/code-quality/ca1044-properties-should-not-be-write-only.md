---
title: 'CA1044: 속성에는 쓰기 전용를 사용 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 444081d1e55bd76b67162add508d4f78415e4b3b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68143202"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: 속성은 쓰기 전용이면 안 됩니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 속성 set 접근자가 없는 get 접근자입니다.

## <a name="rule-description"></a>규칙 설명
 Get 접근자 속성에 대 한 읽기 액세스를 제공 및 set 접근자에는 쓰기 액세스 권한을 제공 합니다. 읽기 전용 속성을 사용하는 것은 가능하고 종종 필요하기도 하지만 쓰기 전용 속성의 사용은 금지되어 있습니다. 이므로이 값을 설정 하는 사용자 수 있도록 하 고 값을 보기에서 사용자를 방지 모든 보안을 제공 하지 않습니다. 또한 읽기 권한이 없으면 공유 개체의 상태를 볼 수 없으므로 사용하는 데 제한을 받습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 속성에 get 접근자를 추가 합니다. 쓰기 전용 속성의 동작이 필요한 경우에이 속성을 메서드로 변환할 수도 있습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 표시 하지 않는 것이 좋습니다.

## <a name="example"></a>예제
 다음 예에서 `BadClassWithWriteOnlyProperty` 쓰기 전용 속성을 사용 하 여 형식입니다. `GoodClassWithReadWriteProperty` 수정 된 코드를 포함합니다.

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]
