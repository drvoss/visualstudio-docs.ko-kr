---
title: 'CA1050: 네임 스페이스에 형식을 선언 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1050
- DeclareTypesInNamespaces
helpviewer_keywords:
- DeclareTypesInNamespaces
- CA1050
ms.assetid: 1002748d-ac8d-404f-85dd-7a12d1ad3e05
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f13684df70db7026e874bc8edb6282faca2cf98d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200539"
---
# <a name="ca1050-declare-types-in-namespaces"></a>CA1050: 네임스페이스에 형식을 선언하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DeclareTypesInNamespaces|
|CheckId|CA1050|
|범주|Microsoft.Design|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 Public 또는 protected 형식이 명명된 된 네임 스페이스 범위 밖에 서 정의 됩니다.

## <a name="rule-description"></a>규칙 설명
 형식 이름 충돌을 방지 하기 위해 네임 스페이스에서 및 관련된 형식을 개체 계층을 구성 하는 방법으로 선언 됩니다. 명명된 된 네임 스페이스 외부에 있는 형식은 코드에서 참조할 수 없는 전역 네임 스페이스에서입니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 형식 네임 스페이스에 배치 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서 경고를 표시 하지 않으려면 필요가 있지만 어셈블리가 다른 어셈블리와 함께 사용 하지 않을 때 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 네임 스페이스 외부에 잘못 선언 형식을 갖는 라이브러리와 이름이 같은 네임 스페이스에서 선언 하는 형식을 보여 줍니다.

 [!code-csharp[FxCop.Design.TypesLiveInNamespaces#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/cs/FxCop.Design.TypesLiveInNamespaces.cs#1)]
 [!code-vb[FxCop.Design.TypesLiveInNamespaces#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TypesLiveInNamespaces/vb/FxCop.Design.TypesLiveInNamespaces.vb#1)]

## <a name="example"></a>예제
 이전에 정의 된 라이브러리를 사용 하는 다음 응용 프로그램입니다. 네임 스페이스 외부 선언 된 형식을 생성 될 때 이름 `Test` 네임 스페이스로 한정 되지 않습니다. 또한 액세스 하는 `Test` 입력 `Goodspace`, 네임 스페이스 이름은 필수입니다.

 [!code-csharp[FxCop.Design.TestTypesLive#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/cs/FxCop.Design.TestTypesLive.cs#1)]
 [!code-vb[FxCop.Design.TestTypesLive#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.TestTypesLive/vb/FxCop.Design.TestTypesLive.vb#1)]
