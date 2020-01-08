---
title: 관리 코드에 대해 전체 솔루션 분석 사용 & 사용 안 함
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d699dd74315cfc36820c1cdb4120543e0290b1a1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587513"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>방법: 관리 코드에 대 한 전체 솔루션 분석 사용 및 사용 안 함

*전체 솔루션 분석* 이란 코드 분석이 편집기에서 열려 있는지 C# 여부에 관계 없이 솔루션의 모든 또는 Visual Basic 파일을 검사 하는 것을 의미 합니다. 기본적으로 전체 솔루션 분석은 Visual Basic 및에 대해 C#사용 *되지 않도록* *설정* 됩니다.

모든 파일의 모든 문제를 확인 하는 것이 유용할 수 있지만 혼동 될 수도 있습니다. 솔루션이 매우 크거나 파일이 많은 경우 Visual Studio가 느려질 수 있습니다. 표시 되는 문제 수를 제한 하 고 Visual Studio 성능을 향상 시키려면 전체 솔루션 분석을 사용 하지 않도록 설정할 수 있습니다. 필요한 경우이 기능을 쉽게 다시 활성화할 수 있습니다.

다음 그림에서 전체 솔루션 분석을 사용 하도록 설정 합니다. 솔루션에 있는 모든 파일의 컴파일러 및 코드 분석 문제는 열려 있지 않은 경우에도 표시 됩니다.

![전체 솔루션 분석을 사용 하도록 설정 했습니다.](../code-quality/media/fsa_enabled.png)

다음 이미지는 전체 솔루션 분석을 사용 하지 않도록 설정한 후 동일한 솔루션의 결과를 보여 줍니다. 열려 있는 솔루션 파일의 컴파일러 오류 및 코드 분석 문제도 오류 목록에 표시 됩니다.

![전체 솔루션 분석을 사용 하지 않습니다.](../code-quality/media/fsa_disabled.png)

## <a name="toggle-full-solution-analysis"></a>전체 솔루션 분석 설정/해제

1. **옵션** 대화 상자를 열려면 Visual Studio의 메뉴 모음에서 **도구** > **옵션**을 선택 합니다.

1. **옵션** 대화 상자에서 **텍스트 편집기** > **C#** 또는 **기본** > **고급**을 선택 합니다.

1. 전체 솔루션 분석 **사용** 확인란을 선택 하 여 전체 솔루션 분석을 사용 하도록 설정 하거나 확인란의 선택을 취소 하 여 사용 하지 않도록 설정 합니다. 완료 되 면 **확인을** 선택 합니다.

   ![전체 솔루션 분석 사용 확인란을 선택 합니다.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="automatically-disable-full-solution-analysis"></a>자동으로 전체 솔루션 분석 사용 안 함

Visual Studio에서 200 MB 이하의 시스템 메모리를 사용할 수 있음을 감지 하면 사용 하도록 설정 된 경우 전체 솔루션 분석 (및 기타 일부 기능)을 자동으로 비활성화 합니다. 이 문제가 발생 하는 경우 Visual Studio에서 일부 기능을 사용 하지 않도록 설정 했다는 알림이 표시 됩니다. 원하는 경우 단추를 사용 하 여 전체 솔루션 분석을 다시 활성화할 수 있습니다.

![전체 솔루션 분석을 일시 중단 하는 경고 텍스트](../code-quality/media/fsa_alert.png)
