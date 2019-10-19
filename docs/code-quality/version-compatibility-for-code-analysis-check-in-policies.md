---
title: 코드 분석 체크 인 정책에 대한 버전 호환성
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8385e2b36d09f029c4b8625e58cd99ecc06ea226
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649020"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>코드 분석 체크 인 정책에 대한 버전 호환성

서로 다른 버전의 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]을 사용 하 여 코드 분석 체크 인 정책을 평가 하 고 작성 해야 하는 경우에는 [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] 및 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 확인 정책 평가 방법의 차이점을 알아야 합니다.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>체크 인 정책 평가에 대 한 버전 호환성

- @No__t_0에서 코드 분석 체크 인 정책을 평가 하는 경우 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]에는 있지만 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]에 존재 하지 않는 모든 규칙은 무시 됩니다.

- @No__t_0에서 코드 분석 체크 인 정책을 평가 하는 경우 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 전용으로 적용 되는 모든 새 규칙은 무시 됩니다.

- 코드 분석 체크 인 정책에서 규칙 어셈블리를 지정 하는 경우 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]는 인식할 수 없는 어셈블리에 지정 된 모든 규칙을 무시 합니다.

- 코드 분석 체크 인 정책에서 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 인식 하지 못하는 규칙 어셈블리를 지정 하는 경우 메시지가 표시 됩니다.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>체크 인 정책 작성에 대 한 버전 호환성

- @No__t_0 버전의 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]를 사용 하 여 코드 분석 체크 인 정책을 만든 경우 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] 버전의 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]를 사용 하 여 수정할 수 없습니다. 또한 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]는 정책을 평가할 수 없습니다.

- @No__t_1에서 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]를 사용 하 여 코드 분석 체크 인 정책을 만든 경우 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]에서 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]를 사용 하 여 수정할 수 있으며, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]에서 정책을 평가할 수도 있습니다. @No__t_1에서 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]를 사용 하 여 정책을 수정한 후 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]에서 [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]를 사용 하 여 정책을 편집할 수 없습니다. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]은 강력한 이름이 일치하지 않는 문제 없이 정책을 평가할 수 있습니다.

- @No__t_0 및 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] 모두에 적용 되는 규칙 설정을 사용 하 여 코드 분석 체크 인 정책을 만들려면 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]에서 정책을 만들고 필요한 사항을 모두 변경한 다음 정책을 저장 해야 합니다. 규칙에 대 한 변경 내용이 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]에만 존재 하는 경우 [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]에서 정책을 수정 하 고 저장 합니다.

   @No__t_0에서 정책을 저장 한 후에는 [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]에 있는 규칙에 대 한 설정을 더 이상 변경할 수 없습니다.
