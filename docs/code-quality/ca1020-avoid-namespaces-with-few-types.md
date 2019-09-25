---
title: 'CA1020: 형식이 부족한 네임스페이스를 사용하지 마세요.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e5c50f607253304b05dd7ab9350646a0df05e70
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236238"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: 형식이 부족한 네임스페이스를 사용하지 마세요.

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|범주|Microsoft.Design|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인

전역 네임 스페이스 이외의 네임 스페이스에는 5 개 미만의 형식이 포함 되어 있습니다.

## <a name="rule-description"></a>규칙 설명

각 네임 스페이스에 논리적 구성이 있는지 확인 하 고, 잘못 된 형식의 네임 스페이스에 형식을 저장 하는 유효한 이유가 있는지 확인 합니다. 네임 스페이스는 대부분의 시나리오에서 함께 사용 되는 형식을 포함 해야 합니다. 응용 프로그램을 함께 사용할 수 없는 경우 형식은 별도의 네임 스페이스에 있어야 합니다. 예 <xref:System.Web.UI> 를 들어 네임 스페이스에는 웹 응용 프로그램에 사용 되는 형식이 포함 <xref:System.Windows.Forms> 되 고, 네임 스페이스에는 [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]기반 응용 프로그램에서 사용 되는 형식이 포함 되어 있습니다. 두 네임스페이스에 사용자 인터페이스의 특성을 제어하는 형식이 포함되었더라도 이러한 형식은 동일한 애플리케이션에서 사용하도록 디자인되지 않았습니다. 따라서 별도의 네임스페이스에 배치됩니다. 신중한 네임 스페이스 조직은 기능의 검색 가능성을 높이기 때문에 유용할 수도 있습니다. 라이브러리 소비자는 네임 스페이스 계층 구조를 검사 하 여 기능을 구현 하는 형식을 찾을 수 있어야 합니다.

> [!NOTE]
> 이 지침을 준수 하기 위해 디자인 타임 형식 및 사용 권한을 다른 네임 스페이스로 병합 해서는 안 됩니다. 이러한 형식은 기본 네임 스페이스 아래의 고유한 네임 스페이스에 속하며 네임 스페이스는 각각 `.Design` 및 `.Permissions`로 끝나야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 몇 가지 형식만 포함 하는 네임 스페이스를 단일 네임 스페이스로 결합 하십시오.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

네임 스페이스에 다른 네임 스페이스의 형식과 함께 사용 되는 형식이 포함 되지 않은 경우에는이 규칙에서 경고를 표시 하지 않는 것이 안전 합니다.