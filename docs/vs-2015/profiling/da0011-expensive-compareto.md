---
title: 'DA0011: CompareTo의 부담이 큽니다. | Microsoft Docs'
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
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af5797a9e3939d3163d6d1cee9719f38036543ab
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51720857"
---
# <a name="da0011-expensive-compareto"></a>DA0011: CompareTo의 부담이 큽니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017에서 최신 설명서를 참조 하세요 [DA0011: CompareTo의 부담이 큽니다](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto) docs.microsoft.com에서 제공 합니다.  
  
|||  
|-|-|  
|규칙 ID|DA0011|  
|범주|.NET Framework 사용|  
|프로파일링 방법|샘플링<br /><br /> .NET 메모리|  
|메시지|CompareTo 함수는 정리되어야 하며 메모리를 할당하면 안 됩니다. 가능한 경우 CompareTo 함수의 복잡성을 줄입니다.|  
|규칙 유형|경고|  
  
## <a name="cause"></a>원인  
 해당 형식의 CompareTo 메서드가 부담이 크거나 메모리를 할당합니다.  
  
## <a name="rule-description"></a>규칙 설명  
 CompareTo 메서드는 효율적이어야 하며 메모리를 할당하지 않아야 합니다.  
  
## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법  
 CompareTo 메서드의 복잡성을 줄이세요.

