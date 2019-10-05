---
title: 코드 분석 규칙 집합 참조 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
helpviewer_keywords:
- code analysis, rule sets
ms.assetid: 5874e854-e298-4d2e-bbe4-95e899d22587
caps.latest.revision: 45
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a1f91b352da5a41ec2ef81fb6067976073c787ef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62576756"
---
# <a name="code-analysis-rule-set-reference"></a>코드 분석 규칙 집합 참조
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

관리 되는 코드 프로젝트에 대 한 코드 분석을 구성 하는 경우 [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], 또는 [!INCLUDE[vsPro](../includes/vspro-md.md)]의 기본 제공 목록으로 표시 됩니다 *규칙 집합*합니다. 표준 규칙 집합 중 하나를 사용하거나 프로젝트 요구 사항에 맞게 규칙 집합을 사용자 지정할 수 있습니다.  
  
## <a name="available-rule-sets"></a>사용 가능한 규칙 집합  
 다음 표에는 기본 규칙 집합이 나열됩니다.  
  
|||  
|-|-|  
|[모든 규칙 규칙 집합](../code-quality/all-rules-rule-set.md)|이 규칙 집합에는 모든 규칙이 포함 되어 있습니다. 이 규칙 집합 실행을 많은 수의 경고가 보고 될 수 있습니다. 코드에서 모든 문제의 포괄적인 그림을 인식 하도록 설정 하려면이 규칙을 사용 합니다. 이 결정 하는 더욱 중점 둔된 규칙의 집합은 프로젝트에 대 한 실행에 가장 적합 한 수 있습니다.|  
|[관리 코드에 대한 기본 수정 규칙 규칙 집합](../code-quality/basic-correctness-rules-rule-set-for-managed-code.md)|이러한 규칙은 논리 오류 및 일반적인 실수 프레임 워크 Api 사용에 초점을 둡니다. 최소 권장된 규칙에 의해 보고 된 경고 목록을 확장 하려면이 규칙 집합을 포함 합니다.|  
|[관리 코드에 대한 기본 디자인 지침 규칙 규칙 집합](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md)|이러한 규칙은 코드를 더 쉽게 이해 하 고 사용 하기 위한 모범 사례 적용 초점입니다. 프로젝트에 라이브러리 코드가 있거나 유지 관리를 쉽게 코드에 대 한 모범 사례를 적용 하려는 경우이 규칙 집합을 포함 합니다.|  
|[관리 코드에 대한 확장 수정 규칙 규칙 집합](../code-quality/extended-correctness-rules-rule-set-for-managed-code.md)|이러한 규칙을 보고 하는 논리 및 프레임 워크 사용 오류를 최대화 하기 위해 기본 수정 규칙 확장 합니다. COM interop 및 모바일 응용 프로그램 같은 특정 시나리오에 주안점을 둡니다. 프로젝트 또는 프로젝트의 추가 문제 찾기 이러한 시나리오 중 하나가 적용 되는 경우이 규칙 집합을 포함 하는 것이 좋습니다.|  
|[관리 코드에 대한 확장 디자인 지침 규칙 규칙 집합](../code-quality/extended-design-guidelines-rules-rule-set-for-managed-code.md)|이러한 규칙을 보고 되는 유용성 및 유지 관리 문제를 최대화 하기 위해 기본 디자인 지침 규칙 확장 합니다. 명명 지침에 주안점을 둡니다. 프로젝트에 라이브러리 코드가 있거나 유지 관리 가능한 코드를 작성 하는 데 가장 높은 표준을 적용 하려는 경우이 규칙 집합을 포함 하는 것이 좋습니다.|  
|[관리 코드에 대한 전역화 규칙 규칙 집합](../code-quality/globalization-rules-rule-set-for-managed-code.md)|이러한 규칙은 다른 언어, 로캘 및 문화권에서 사용 될 때 올바로 표시 응용 프로그램에서 데이터를 방해 하는 문제에 집중 합니다. 응용 프로그램 지역화 되거나 전역화 하는 경우이 규칙 집합을 포함 합니다.|  
|[관리 코드에 대한 관리 최소 규칙 규칙 집합](../code-quality/managed-minimun-rules-rule-set-for-managed-code.md)|이러한 규칙은 코드 분석은 가장 정확한 코드의 가장 중요 한 문제에 집중 합니다.  이러한 규칙은 수 적으며 제한 된 Visual Studio 버전에서 실행 하기 위해서만 합니다.  다른 Visual Studio 버전을 사용 하 여 MinimumRecommendedRules.ruleset을 사용 합니다.|  
|[관리 코드에 대한 관리 권장 규칙 규칙 집합](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)|이러한 규칙은 잠재적 보안 허점, 응용 프로그램 충돌 및 기타 중요 한 논리 및 디자인 오류를 비롯 하 여 코드의 가장 중요 한 문제에 집중 합니다. 프로젝트에 대해 만든 모든 사용자 지정 규칙 집합에 설정 합니다.이 규칙을 포함 해야 합니다.|  
|[혼합 최소 규칙 규칙 집합](../code-quality/mixed-minimum-rules-rule-set.md)|이러한 규칙의 가장 중요 한 문제에 초점을 맞춥니다에 C++ 잠재적 보안 허점 및 응용 프로그램 작동 중단을 포함 하 여 공용 언어 런타임을 지 원하는 프로젝트입니다. 이 규칙 집합에 대해 만든 모든 사용자 지정 규칙 집합에 포함 해야 하면 C++ 공용 언어 런타임에서 지 원하는 프로젝트입니다.|  
|[혼합 권장 규칙 규칙 집합](../code-quality/mixed-recommended-rules-rule-set.md)|이러한 규칙의 가장 일반적인 및 중요 한 문제에 초점을 맞춥니다에 C++ 잠재적 보안 허점, 응용 프로그램 충돌 및 기타 중요 한 논리 및 디자인 오류를 포함 하 여 공용 언어 런타임을 지 원하는 프로젝트입니다. 이 규칙 집합에 대해 만든 모든 사용자 지정 규칙 집합에 포함 해야 하면 C++ 공용 언어 런타임에서 지 원하는 프로젝트입니다.  이 규칙 집합은 Visual Studio Professional edition 이상 구성 하도록 설계 되었습니다.|  
|[네이티브 최소 규칙 규칙 집합](../code-quality/native-minimum-rules-rule-set.md)|이러한 규칙은 잠재적 보안 허점 및 응용 프로그램 충돌을 비롯 하 여 네이티브 코드의 가장 중요 한 문제에 집중 합니다. 네이티브 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에 이 규칙 집합을 포함해야 합니다.|  
|[네이티브 권장 규칙 규칙 집합](../code-quality/native-recommended-rules-rule-set.md)|이러한 규칙은 잠재적 보안 허점 및 응용 프로그램 충돌을 비롯 하 여 네이티브 코드의 가장 중요 하 고 일반적인 문제에 집중 합니다.  네이티브 프로젝트에 대해 만드는 모든 사용자 지정 규칙 집합에 이 규칙 집합을 포함해야 합니다.  이 규칙 집합은 Visual Studio Professional edition 이상 작동 하도록 설계 되었습니다.|  
|[관리 코드에 대한 보안 규칙 규칙 집합](../code-quality/security-rules-rule-set-for-managed-code.md)|이 규칙 집합에는 모든 Microsoft 보안 규칙이 포함 되어 있습니다. 보고 되는 잠재적인 보안 문제 수를 최대화 하려면이 규칙 집합을 포함 합니다.|
