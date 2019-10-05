---
title: 'CA1713: 이벤트에는 before 또는 after 접두사 없어야 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6a36f9c8ce788b30f14d8ca0ce9d565ab45975a5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62535206"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: 이벤트에 Before 또는 After 접두사를 사용하지 마세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|범주|Microsoft.Naming|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 이벤트의 이름이 'Before' 또는 '사후'로 시작 합니다.

## <a name="rule-description"></a>규칙 설명
 이벤트 이름에는 이벤트를 발생 시키는 작업을 설명 해야 합니다. 특정 시퀀스에서 발생하는 관련 이벤트의 이름을 지정하려면 현재 또는 과거 시제를 사용하여 동작 시퀀스 내의 상대적인 위치를 나타냅니다. 예를 들어, 이벤트 쌍 이름이 발생 하면 리소스를 닫을 때 이름을 지정할 수 있습니다 것 '닫는' 및 '종결' 대신 'BeforeClose' 및 'AfterClose'.

 명명 규칙은 공통 된 모양을 라이브러리에 대 한 해당 공용 언어 런타임을 대상으로 합니다. 이렇게 하면 새 소프트웨어 라이브러리에 대 한 필수 항목이 며 관리 코드 개발의 전문 지식을 가진 사람이 라이브러리를 개발 하는 고객 신뢰도 증가 하는 학습 곡선을 줄어듭니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이벤트 이름에서 접두사를 제거 하 고 현재 또는 과거 시제 동사를 사용 하 여 이름을 변경 하는 것이 좋습니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다.
