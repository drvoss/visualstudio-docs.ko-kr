---
title: 'CA1711: 식별자에는 접미사를 사용 해야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c0ed08a50ce7e4c665839f6dccb4913e13d0d774
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65676481"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: 식별자에는 올바른 접미사를 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|범주|Microsoft.Naming|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 식별자에는 접미사입니다.

## <a name="rule-description"></a>규칙 설명
 규칙에 따라 특정 기본 형식을 확장 하거나 특정 인터페이스 또는 이러한 형식에서 파생 된 형식을 구현 하는 형식의 이름만 예약 된 특정 접미사로 끝나야 합니다. 다른 형식 이름에는 이러한 예약된 접미사를 사용하면 안 됩니다.

 다음 표에서 예약 된 접미사 및 기본 형식 및 연결 된 인터페이스를 나열 합니다.

|접미사|기본 형식/인터페이스|
|------------|--------------------------|
|특성|<xref:System.Attribute?displayProperty=fullName>|
|컬렉션|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|사전|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|이벤트 처리기|이벤트 처리기 대리자를|
|예외|<xref:System.Exception?displayProperty=fullName>|
|사용 권한|<xref:System.Security.IPermission?displayProperty=fullName>|
|Queue|<xref:System.Collections.Queue?displayProperty=fullName>|
|스택|<xref:System.Collections.Stack?displayProperty=fullName>|
|스트림|<xref:System.IO.Stream?displayProperty=fullName>|

 또한 다음 접미사 해야 **되지** 사용:

- 대리자

- Enum

- -Impl '핵심'를 대신 사용

- 같은 형식의 이전 버전을 구분 하기 위해 Ex 또는 유사한 접미사

  명명 규칙은 공통 된 모양을 라이브러리에 대 한 해당 공용 언어 런타임을 대상으로 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 대 한 필수 항목이 며 관리 코드 개발의 전문 지식을 가진 사람이 라이브러리를 개발 하는 고객 신뢰도 증가 하는 학습 곡선을 줄어듭니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 형식 이름에서 접미사를 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 접미사가 애플리케이션 도메인에서 명확한 의미를 갖지 않는 한 이 규칙의 경고를 숨기지 마십시오.

## <a name="related-rules"></a>관련된 규칙
 [CA1710: 식별자에는 올바른 접미사를 사용 해야 합니다.](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>참고 항목
 [특성](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: 이벤트 및 대리자](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
