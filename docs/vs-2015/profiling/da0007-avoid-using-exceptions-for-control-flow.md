---
title: 'DA0007: 제어 흐름에는 예외를 사용하지 마십시오. | Microsoft 문서'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAExceptionsThrown
- vs.performance.7
- vs.performance.rules.DA0007
- vs.performance.DA0007
ms.assetid: ee8ba8b5-2313-46c9-b129-3f3a2a232898
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a86c36c55d11f91daff8e876e852daed2f222307
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737092"
---
# <a name="da0007-avoid-using-exceptions-for-control-flow"></a>DA0007: 제어 흐름에는 예외를 사용하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

규칙 Id | DA0007 |  
| 범주. NET Framework 사용 |  
| 프로 파일링 방법 | 모든 |  
| 메시지 | 많은 수의 예외가 지속적으로 throw 되 고 있습니다. 프로그램 논리에서 예외 사용을 줄여 보세요. |  
| 메시지 유형 | 경고 |  
  
 샘플링, .NET 메모리 또는 리소스 경합 방법을 사용하여 프로파일링할 경우 이 규칙을 트리거하려면 25개 이상의 샘플을 수집해야 합니다.  
  
## <a name="cause"></a>원인  
 프로파일링 데이터에서 .NET Framework 예외 처리기가 호출되는 비율이 높았습니다. throw되는 예외 수를 줄일 때 다른 제어 흐름 논리를 사용해 보세요.  
  
## <a name="rule-description"></a>규칙 설명  
 오류와 프로그램 예외를 중단하는 다른 이벤트를 catch할 때 예외 처리기를 사용하는 것이 좋지만 예외 처리기를 일반 프로그램 실행 논리의 일부로 사용하는 것은 부담이 클 수 있으므로 피해야 합니다. 대부분은 자주 발생하지 않고 예상되지 않는 상황에만 예외를 사용해야 합니다. 일반 프로그램 흐름의 일부로 값을 반환하려면 예외를 사용하면 안 됩니다. 대부분은 값의 유효성을 검사하고 조건부 논리를 사용하여 문제를 일으킨 문의 실행을 중지하는 방식으로 예외 발생을 방지할 수 있습니다.  
  
 자세한 내용은 MSDN의 **Microsoft Patterns and Practices** 라이브러리에 있는 **.NET 응용 프로그램 성능 및 확장성 향상** 볼륨에서 **5장 - 관리되는 코드 성능 향상**의 [예외 관리](http://go.microsoft.com/fwlink/?LinkID=177825) 섹션을 참조하세요.  
  
## <a name="how-to-investigate-a-warning"></a>경고를 조사하는 방법  
 [오류 목록] 창에서 메시지를 두 번 클릭하여 표시 뷰로 이동합니다. **.NET CLR Exceptions(@ProcessInstance)\\# of Exceps Thrown / sec** 측정값이 포함된 열을 찾습니다. 다른 단계보다 예외 처리가 더 빈번한 특정 프로그램 실행 단계가 있는지 확인합니다. 샘플링 프로필을 사용하여 빈번한 예외를 생성하는 throw 문과 try/catch 블록을 확인해 보세요. 필요하면 어떤 예외가 가장 빈번히 처리되는지 파악할 수 있는 논리를 catch 블록에 추가하세요. 가능할 경우 빈번히 실행되는 thorw 문이나 catch 블록을 단순 흐름 제어나 유효성 검사 코드로 바꿉니다.  
  
 예를 들어 응용 프로그램이 빈번한 DivideByZeroException 예외를 처리하는지 확인하려는 경우 0 값으로 분모가 있는지 확인하는 논리를 프로그램에 추가하면 응용 프로그램의 성능이 향상됩니다.



