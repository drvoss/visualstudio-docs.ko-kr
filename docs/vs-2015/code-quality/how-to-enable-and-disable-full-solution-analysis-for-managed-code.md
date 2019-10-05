---
title: '방법: 사용 하도록 설정 하 고 관리 되는 코드에 대 한 전체 솔루션 분석 사용 안 함 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: df06a17ecc093cf24a64e7c3aa11a096a61ee44f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436834"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>방법: 사용 하도록 설정 하 고 관리 되는 코드에 대 한 전체 솔루션 분석 사용 안 함
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> 이 항목에서는 이상 Visual Studio 2015 업데이트 3 RC에만 적용 됩니다.  
  
 *전체 옵션 분석* 솔루션 또는 솔루션에서 Visual C# 또는 Visual Basic 파일 열기와 닫힌 열고 Visual C# 또는 Visual Basic 파일에만 코드 분석 문제를 확인할 수 있는지 여부를 선택할 수 있도록 Visual Studio 기능입니다.  
  
 모든 파일에서 모든 문제를 볼 수 유용 하지만, 솔루션 매우 크거나 많은 파일을 경우 산만 해지고도 Visual Studio 느리게 수 있습니다.  표시 된 문제 수를 제한 하 고 Visual Studio 성능을 개선 하려면 전체 솔루션 분석을 비활성화할 수 있습니다. 원하는 경우 손쉽게이 기능을 다시 활성화할 수 있습니다.  
  
#### <a name="to-toggle-full-solution-analysis"></a>전체 솔루션 분석을 설정/해제 하려면  
  
1. Visual Studio의 주 메뉴에서 선택 **도구** &#124; **옵션** 보려는 합니다 **옵션** 대화 상자.  
  
2. 에 **옵션** 대화 상자에서 **텍스트 편집기** &#124; **C#** 또는 **Basic** &#124; **고급**.  
  
3. 선택 된 **전체 솔루션 분석 사용** 전체 솔루션 분석 사용 하거나 사용 하지 않도록 확인란의 선택을 취소 하려면 확인란 합니다. 선택 된 **확인** 완료 되 면 단추입니다.  
  
     ![전체 솔루션 분석 사용 확인란을 사용 하도록 설정 합니다. ](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>전체 솔루션 분석 사용 하지 않도록 설정 하 고 결과  
 다음 스크린 샷에서 전체 솔루션 분석 사용 하는 경우 결과 볼 수 있습니다. 모든 오류 및에서 코드 분석 문제가 *모든* 솔루션에 있는 파일의 표시 여부에 관계 없이 파일을 열고 여부.  
  
 ![전체 솔루션 분석 사용 하도록 설정 합니다. ](../code-quality/media/fsa-enabled.png "FSA_Enabled")  
  
 다음 스크린 샷에서 전체 솔루션 분석을 해제 한 후 동일한 솔루션에서 결과 보여 줍니다. 오류 및의 코드 분석 문제를 오류 목록에 파일이 표시 하는 솔루션을 엽니다.  
  
 ![전체 솔루션 분석 사용 하지 않도록 설정 합니다. ](../code-quality/media/fsa-disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>자동으로 전체 솔루션 분석 사용 안 함  
 Visual Studio를 검색 하는 경우 200 MB 또는 사용 가능한 시스템 메모리의 이하인 경우, 자동으로 비활성화 전체 솔루션 분석 (뿐만 아니라 다른 기능) 사용 하는 경우. 이 경우이 알리는 경고가 나타납니다. 단추를 사용 하면 작업을 수행 하려는 경우 전체 솔루션 분석을 다시 사용 하도록 설정 합니다.  
  
 ![경고 텍스트에서 전체 솔루션 분석을 일시 중단](../code-quality/media/fsa-alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>추가 세부 정보  
 기본적으로 전체 솔루션 분석 Visual Basic의 경우 사용 하도록 설정 되어 Visual C#을 사용할 수 없습니다.  
  
 Visual Studio 업데이트 3 RC는 크게 메모리 사용량을 줄이고 전체 솔루션 분석 사용 하도록 설정 하는 경우에 유휴, CPU 시간을 감소 하는 향상 된 코드 분석기 진단 v2 엔진을 포함 합니다.
