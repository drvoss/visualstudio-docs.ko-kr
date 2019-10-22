---
title: 이식성 경고
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3e1959066f81663d66e8af2af8039080d8cace6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649126"
---
# <a name="portability-warnings"></a>이식성 경고
이식성 경고는 다양 한 운영 체제 간의 이식성을 지원 합니다.

## <a name="in-this-section"></a>단원 내용

|규칙|설명|
|----------|-----------------|
|[CA1900: 값 형식 필드는 이식 가능해야 합니다.](../code-quality/ca1900.md)|이 규칙은 명시적 레이아웃 특성을 사용 하 여 선언 된 구조체가 64 비트 운영 체제에서 비관리 코드로 마샬링될 때 올바르게 정렬 되는지 확인 합니다.|
|[CA1901: P/Invoke 선언은 이식 가능해야 합니다.](../code-quality/ca1901.md)|이 규칙은 각 매개 변수의 크기와 P/Invoke의 반환 값을 평가 하 고 32 비트 및 64 비트 운영 체제에서 비관리 코드로 마샬링될 때 크기가 올바른지 확인 합니다.|
|[CA1903: 대상 프레임워크에서 API만 사용하십시오.](../code-quality/ca1903.md)|멤버 또는 형식이 프로젝트의 대상 프레임워크에 함께 포함되지 않은 서비스 팩에 도입된 멤버 또는 형식을 사용합니다.|
