---
title: 사용 및 관리 코드에 대 한 전체 솔루션 분석 사용 안 함
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a445439014e3b1f68b634865265089eb68e790a6
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66260884"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>방법: 관리 코드에 대 한 전체 솔루션 분석 활성화 및 비활성화

*전체 솔루션 분석* 열고 시각적 개체에만 코드 분석 문제를 볼 수 있도록 Visual Studio 기능은 C# 또는 Visual Basic 파일용 솔루션 또는 접근할 수 있는 코드 파일. 기본적으로 전체 솔루션 분석은 *사용 하도록 설정* Visual basic의 경우 및 *비활성화* 시각적 개체에 C#.

모든 파일에서 모든 문제를 확인 하려면 유용할 수 있지만 산만 수도 있습니다. 느려집니다 Visual Studio 솔루션이 매우 크거나 파일이 많은 경우. 표시 된 문제 수를 제한 하 고 Visual Studio 성능을 개선 하려면 전체 솔루션 분석을 비활성화할 수 있습니다. 필요한 경우이 기능을 쉽게 다시 활성화할 수 있습니다.

## <a name="to-toggle-full-solution-analysis"></a>전체 솔루션 분석을 설정/해제 하려면

1. 열려는 합니다 **옵션** Visual Studio의 메뉴 모음에서 대화 상자에서 선택 **도구** > **옵션**합니다.

1. 에 **옵션** 대화 상자에서 **텍스트 편집기**  >  **C#** 하거나 **기본**  >  **고급**합니다.

1. 선택 된 **전체 솔루션 분석 사용** 전체 솔루션 분석 사용 하거나 사용 하지 않도록 확인란의 선택을 취소 하려면 확인란 합니다. 선택할 **확인** 완료 되 면 합니다.

    ![전체 솔루션 분석 사용 확인란을 사용 하도록 설정 합니다.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>전체 솔루션 분석 사용 하지 않도록 설정 하 고 결과

다음 스크린 샷에서 전체 솔루션 분석 사용 하는 경우 결과 볼 수 있습니다. 모든 오류 및에서 코드 분석 문제가 *모든* 솔루션에 있는 파일의 표시 여부에 관계 없이 파일을 열고 여부.

![전체 솔루션 분석 사용 하도록 설정 합니다.](../code-quality/media/fsa_enabled.png)

다음 스크린 샷에서 전체 솔루션 분석을 해제 한 후 동일한 솔루션에서 결과 보여 줍니다. 오류 및 열려 있는 솔루션 파일의 코드 분석 문제를 표시 합니다 **오류 목록**합니다.

![전체 솔루션 분석 사용 하지 않도록 설정 합니다.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>자동으로 전체 솔루션 분석 사용 안 함

Visual Studio를 검색 하는 경우 200 MB 또는 사용 가능한 시스템 메모리의 이하인 경우, 자동으로 비활성화 전체 솔루션 분석 (및 다른 기능) 사용 하는 경우. 이 경우 Visual Studio에 사용 하지 않도록 몇 가지 기능에 알리는 경고가 나타납니다. 단추를 사용 하면 원하는 경우 전체 솔루션 분석 사용 하도록 다시 설정할 수 있습니다.

![전체 솔루션 분석을 일시 중단 하는 경고 텍스트](../code-quality/media/fsa_alert.png)