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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a6a3557cffec60de91da46f60040ec675c866cbf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825327"
---
# <a name="portability-warnings"></a>이식성 경고
이식성 경고는 여러 운영 체제 간의 이식성을 지원합니다.

## <a name="in-this-section"></a>섹션 내용

|규칙|설명|
|----------|-----------------|
|[CA1900: 값 형식 필드는 이식 가능 해야 합니다.](../code-quality/ca1900-value-type-fields-should-be-portable.md)|이 규칙은 명시적 레이아웃 특성을 사용 하 여 선언 된 구조체가 64 비트 운영 체제에서 비관리 코드로 마샬링될 때 올바르게 맞춰지는지 검사 합니다.|
|[CA1901: P/Invoke 선언은 이식 가능 해야 합니다.](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|이 규칙은 P/Invoke의 반환 값과 각 매개 변수의 크기를 계산 하 고 크기로 32 비트 및 64 비트 운영 체제에서 비관리 코드로 마샬링될 때 정확한 지 확인 합니다.|
|[CA1903: 대상된 프레임 워크에서 API만 사용](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|멤버 또는 형식이 프로젝트의 대상 프레임워크에 함께 포함되지 않은 서비스 팩에 도입된 멤버 또는 형식을 사용합니다.|