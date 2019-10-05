---
title: 'CA1306: 데이터 형식에 대 한 로캘을 설정 하십시오. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1306
- SetLocaleForDataTypes
helpviewer_keywords:
- CA1306
- SetLocaleForDataTypes
ms.assetid: 104297b2-5806-4de0-a8d9-c589380a796c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 75e67cdd058939837441bd969ac8629a6fc65dcc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200366"
---
# <a name="ca1306-set-locale-for-data-types"></a>CA1306: 데이터 형식에 맞는 로캘을 설정하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SetLocaleForDataTypes|
|CheckId|CA1306|
|범주|Microsoft.Globalization|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 하나 이상의 메서드 또는 생성자 생성 <xref:System.Data.DataTable?displayProperty=fullName> 또는 <xref:System.Data.DataSet?displayProperty=fullName> 인스턴스 및 로캘 속성을 명시적으로 설정 되지 않았습니다 (<xref:System.Data.DataTable.Locale%2A?displayProperty=fullName> 또는 <xref:System.Data.DataSet.Locale%2A?displayProperty=fullName>).

## <a name="rule-description"></a>규칙 설명
 로캘을 숫자 값, 통화 기호 및 정렬 순서에 사용 되는 형식 지정과 같은 데이터에 대 한 문화권별 표현 요소를 결정 합니다. 만들 때를 <xref:System.Data.DataTable> 또는 <xref:System.Data.DataSet>, 로캘을 명시적으로 설정 해야 합니다. 기본적으로 이러한 형식에 대 한 로캘을 현재 문화권을 사용 합니다. 데이터베이스 또는 파일에 저장 되 고 전체적으로 공유 하는 데이터에 대 한 로캘을 일반적으로 설정 해야 고정 문화권으로 (<xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>). 문화권에 걸쳐 데이터를 공유 하면 기본 로캘을 사용 하면 내용의 합니다 <xref:System.Data.DataTable> 또는 <xref:System.Data.DataSet> 표시 되거나 올바르게 해석 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면 로캘을 명시적으로 설정 합니다 <xref:System.Data.DataTable> 또는 <xref:System.Data.DataSet>합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 라이브러리 또는 응용 프로그램은 제한 된 로컬 사용자에 대 한 데이터를 공유 하지 않으면, 기본 설정은 모든 지원 되는 시나리오에서 원하는 동작을 만들 때이 규칙에서 경고를 표시 하지 않으려면 안전 합니다.

## <a name="example"></a>예제
 다음 예제에서는 두 개의 <xref:System.Data.DataTable> 인스턴스.

 [!code-csharp[FxCop.Globalization.DataTable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.DataTable/cs/FxCop.Globalization.DataTable.cs#1)]

## <a name="see-also"></a>관련 항목
 <xref:System.Data.DataTable?displayProperty=fullName> <xref:System.Data.DataSet?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>
 <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>
