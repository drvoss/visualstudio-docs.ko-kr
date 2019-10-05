---
title: 'CA1700: 열거형 값 이름을 지정 하지 마세요 &#39;예약&#39; | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1700
- DoNotNameEnumValuesReserved
helpviewer_keywords:
- DoNotNameEnumValuesReserved
- CA1700
ms.assetid: 7a7e01c3-ae7d-4c82-a646-91b58864a749
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a5446d21b51f57b4a614e8931b154654bee99cd2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68189268"
---
# <a name="ca1700-do-not-name-enum-values-39reserved39"></a>CA1700: 열거형 값 이름을 지정 하지 마세요 &#39;예약&#39;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotNameEnumValuesReserved|
|CheckId|CA1700|
|범주|Microsoft.Naming|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 "Reserved" 라는 단어를 포함 하는 열거형 멤버의 이름입니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙에서는 "reserved"라는 단어가 포함된 이름을 갖는 열거형 멤버가 현재 사용되지는 않지만 이후 버전에서 이름이 바뀌거나 제거될 자리 표시자라고 가정합니다. 멤버의 이름을 바꾸거나 멤버를 제거하는 것은 주요 변경에 해당합니다. 이름에 "예약 됨" 또는 사용자 읽기 또는 설명서에서 준수에 대해 사용할 수 있습니다 서 멤버를 무시 하기를 기대할 수 없습니다. 또한 예약 된 멤버 개체 브라우저 및 통합된 개발 환경에서 표시 하기 때문에 혼동 하는 방법에 대 한 멤버는 실제로 사용 중인 울 수 있습니다.

 예약된 된 멤버를 사용 하는 대신 이후 버전에서 열거형에 새 멤버를 추가 합니다. 대부분의 경우에서 새 멤버 추가 아닙니다는 중요 한 변경으로 추가 변경 하려면 원래 멤버 값의 발생 하지 않습니다.

 사례 제한 된 수에서에 멤버 추가 원래 멤버의 원래 값을 유지 하는 경우에 주요 변경 합니다. 기본적으로, 새 멤버 반환할 수 없는 기존 코드 경로에서 사용 하는 호출자를 중단 하지 않고는 `switch` (`Select` 에서 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) 문은 전체 멤버 목록을 포함 하는 및에서 예외를 throw 하는 반환 값에는 기본 경우입니다. 보조 문제는 클라이언트 코드 처리 하는 수 하지 리플렉션 메서드에서 동작의 변화를 같은 <xref:System.Enum.IsDefined%2A?displayProperty=fullName>합니다. 따라서 기존 메서드에서 반환할 새 멤버에 리플렉션 사용으로 인해 발생 하는 알려진된 응용 프로그램 비 호환성, 유일한 해결책 경우:

1. 원래 및 새 멤버를 포함 하는 새 열거형을 추가 합니다.

2. 원래 열거형으로 표시 된 <xref:System.ObsoleteAttribute?displayProperty=fullName> 특성입니다.

   모든 외부에서 표시 되는 형식 또는 원래 열거형을 노출 하는 멤버에 대해 동일한 절차를 따릅니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 제거 하거나 멤버의 이름을 변경 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 라이브러리에 이전에 제공 된 또는 현재 사용 되는 멤버에 대 한이 규칙에서 경고를 표시 하지 않아도 안전 합니다.

## <a name="related-rules"></a>관련된 규칙
 [CA2217: 열거형을 FlagsAttribute로 표시 하지 마십시오.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1712: 열거형 값 형식 이름의 접두사로 사용 하지 마세요](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: 열거형 저장소는 Int32 여야 합니다.](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1008: 열거형 값이 0 이면 있어야 합니다.](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: 열거형을 FlagsAttribute로 표시](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
