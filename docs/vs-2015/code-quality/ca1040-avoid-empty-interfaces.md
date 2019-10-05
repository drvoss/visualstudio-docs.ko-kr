---
title: 'CA1040: 빈 인터페이스 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1040
- AvoidEmptyInterfaces
helpviewer_keywords:
- AvoidEmptyInterfaces
- CA1040
ms.assetid: 120a741b-5fd1-4836-8453-7857e0cd0380
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: bc785967b4e27599b4a04aeb7740b53b5076938d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62559750"
---
# <a name="ca1040-avoid-empty-interfaces"></a>CA1040: 빈 인터페이스를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidEmptyInterfaces|
|CheckId|CA1040|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 인터페이스 멤버를 선언 하지 않거나 두 개 이상의 다른 인터페이스를 구현 합니다.

## <a name="rule-description"></a>규칙 설명
 인터페이스에서는 동작이나 사용 계약을 제공하는 멤버를 정의합니다. 인터페이스에 의해 설명되는 기능은 상속 계층 구조에서 형식이 나타나는 위치에 관계없이 모든 형식에서 사용할 수 있습니다. 형식에서는 인터페이스의 멤버에 대한 구현을 제공하여 인터페이스를 구현합니다. 빈 인터페이스 멤버를 정의 하지 않습니다. 따라서 구현 될 수 있는 계약을 정의 하지 않습니다.

 빈 디자인 포함가 인터페이스를 구현 해야 하는 경우 아마도 인터페이스를 사용 하 여 표식 또는 형식 그룹을 식별 하는 방법으로는 합니다. 이 식별 런타임 시 발생 하는 경우이 작업을 수행 하는 올바른 방법은 사용자 지정 특성을 사용 하는 것입니다. 대상 형식을 식별 하기 위해 존재 여부 또는 특성의 부재 나 특성의 속성을 사용 합니다. 빈 인터페이스를 사용 하는 것이 적합 한 다음 식별 컴파일 타임에 발생 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 인터페이스를 제거 하거나 멤버를 추가 합니다. 빈 인터페이스 형식 집합이 레이블을 사용 중인 경우 사용자 지정 특성을 사용 하 여 인터페이스를 대체 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 컴파일 타임에 형식의 집합을 식별 하기 위해 인터페이스를 사용 하는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 빈 인터페이스를 보여 줍니다.

 [!code-cpp[FxCop.Design.InterfacesNotEmpty#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cpp/FxCop.Design.InterfacesNotEmpty.cpp#1)]
 [!code-csharp[FxCop.Design.InterfacesNotEmpty#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/cs/FxCop.Design.InterfacesNotEmpty.cs#1)]
 [!code-vb[FxCop.Design.InterfacesNotEmpty#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.InterfacesNotEmpty/vb/FxCop.Design.InterfacesNotEmpty.vb#1)]
