---
title: 'CA2103: 명령적 보안 검토 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5b8b3067d5c8ab8204d6ad723315c400e7b27552
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694936"
---
# <a name="ca2103-review-imperative-security"></a>CA2103: 명령적 보안을 검토하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewImperativeSecurity|
|CheckId|CA2103|
|범주|Microsoft.Security|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 메서드가 명령적 보안을 사용하고, 요청이 활성 상태인 동안 변경될 수 있는 반환 값 또는 상태 정보를 사용하여 권한을 구성하고 있습니다.

## <a name="rule-description"></a>규칙 설명
 명령적 보안 관리 되는 개체를 사용 하 여 코드 실행, 사용 권한 및 작업 메타 데이터를 저장 하려면 특성을 사용 하는 선언적 보안을 비교 하는 동안 권한 및 보안 동작을 지정 합니다. 명령적 보안 이므로 유연 하 게 사용 권한 개체의 상태를 설정 하 고 실행된 시간까지 사용할 수 없는 정보를 사용 하 여 보안 동작을 선택할 수 있습니다. 함께 유연성 런타임 정보는 사용 권한의 상태 유지 되지 않습니다 결정 하는 데 사용 하는 동안 그대로 작업이 적용 되는 위험이 따릅니다.

 가능하면 선언적 보안을 사용합니다. 선언적 요청은 이해 하기 쉽습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 사용 권한의 상태 되는 권한으로 변경할 수 있는 정보에 의존 하지 않는 되도록 명령적 보안 요청을 검토 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 사용 권한을 변경 되는 데이터에 의존 하지 않는 경우이 규칙에서 경고를 표시 하지 않아도 안전 합니다. 그러나 선언적 해당 하는 명령적 요청을 변경 하는 것이 좋습니다.

## <a name="see-also"></a>참고 항목
 [보안 코딩 지침](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [데이터 및 모델링](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
