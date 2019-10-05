---
title: 'CA2207: 값 형식 정적 필드를 인라인으로 초기화 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- InitializeValueTypeStaticFieldsInline
- CA2207
helpviewer_keywords:
- CA2207
- InitializeValueTypeStaticFieldsInline
ms.assetid: d1ea9d8b-ecc2-46ca-86e2-c41dd0e76658
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 4f8bc843dc20df03ddf38a7506342addb6477297
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142526"
---
# <a name="ca2207-initialize-value-type-static-fields-inline"></a>CA2207: 값 형식 정적 필드 인라인을 초기화하십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|InitializeValueTypeStaticFieldsInline|
|CheckId|CA2207|
|범주|Microsoft.Usage|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 값 형식에서 명시적인 정적 생성자를 선언합니다.

## <a name="rule-description"></a>규칙 설명
 여기서 모든 값 형식 필드는 0으로 설정 하 고 모든 참조 형식 필드로 설정 되는 기본 초기화 값 형식 선언 되 면 거치게 `null` (`Nothing` Visual basic에서). 명시적인 정적 생성자는 인스턴스 생성자 보다 먼저 실행 되도록 보장 됩니다 또는 형식의 정적 멤버 라고 합니다. 따라서 형식 인스턴스 생성자를 호출 하지 않고 만들어지면 정적 생성자를 실행 하려면 보장 되지 않습니다.

 C# 및 Visual Basic 컴파일러를 추가 하는 경우 모든 정적 데이터를 인라인으로 초기화 하 고 명시적인 정적 생성자가 선언는 `beforefieldinit` MSIL 클래스 정의에 플래그입니다. 컴파일러는 또한 정적 초기화 코드를 포함 하는 개인 정적 생성자를 추가 합니다. 이 개인 정적 생성자는 형식의 모든 정적 필드에 액세스 하기 전에 실행 하도록 보장 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 문제를 해결 하려면이 규칙 위반 선언 되 고 정적 생성자를 제거 하는 경우 모든 정적 데이터를 초기화 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.

## <a name="related-rules"></a>관련된 규칙
 [CA1810: 참조 형식 정적 필드를 인라인으로 초기화](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)
