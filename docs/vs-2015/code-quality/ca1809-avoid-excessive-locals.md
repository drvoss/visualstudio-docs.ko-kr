---
title: 'CA1809: 과도 한 지역 방지 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 64002b9b99d1b861fa3378710cb0bb8d9219c99d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157996"
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: 불필요한 로컬 항목을 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|AvoidExcessiveLocals|
|CheckId|CA1809|
|범주|Microsoft.Performance|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 멤버 중 일부는 컴파일러에서 생성 된 않을 64 개 이상의 지역 변수를 포함 합니다.

## <a name="rule-description"></a>규칙 설명
 대신 라고 하는 메모리에서 프로세서 레지스터에 값을 저장 하는 성능 최적화에 많이 *레지스터* 값입니다. 공용 언어 런타임에서 스택에 푸시됩니다 최대 64 개의 지역 변수를 고려합니다. 높이려면 없는 변수를 스택에 배치 됩니다 및 조작 하기 전에 등록으로 이동 해야 합니다. 기회 수 있도록 모든 지역 변수에 레지스터를 64 개로 로컬 변수 수를 제한 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 리팩터링 64 개 이상 지역 변수를 사용 하 여 구현 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 성능 문제가 없는 경우이 규칙에서 경고를 표시 하거나 규칙을 사용 하지 않도록 설정 해도 됩니다.

## <a name="related-rules"></a>관련된 규칙
 [CA1804: 사용 되지 않는 로컬 항목을 제거](../code-quality/ca1804-remove-unused-locals.md)
