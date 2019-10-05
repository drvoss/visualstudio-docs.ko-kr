---
title: '8단계: 퀴즈를 사용자 지정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 75bde59c6e4b61c2775f188383fc9058a6c31242
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178556"
---
# <a name="step-8-customize-the-quiz"></a>8단계: 퀴즈 사용자 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

자습서의 마지막 부분에서는 퀴즈를 사용자 지정하고 이미 배운 내용을 확장하는 몇 가지 방법을 살펴보겠습니다. 예를 들어 프로그램에서 답이 분수가 아닌 난수 나누기 문제를 만드는 방법을 생각해 보세요. 자세히 알아보려면 `timeLabel` 컨트롤을 다른 색으로 바꾸고 퀴즈를 푸는 사람에게 힌트를 제공합니다.  
  
### <a name="to-customize-the-quiz"></a>퀴즈를 사용자 지정하려면  
  
- 퀴즈에서 남은 시간이 5초뿐이라면 **BackColor** 속성(`timeLabel.BackColor = Color.Red;`)을 설정하여 **timeLabel** 컨트롤을 빨간색으로 바꿉니다. 퀴즈가 끝나면 색을 초기화합니다.  
  
- NumericUpDown 컨트롤에 정답이 입력되면 소리를 재생하여 퀴즈를 푸는 사람에게 힌트를 제공합니다. 각 컨트롤의 `ValueChanged()` 이벤트에 대한 이벤트 처리기를 작성해야 합니다. 이 이벤트는 퀴즈를 푸는 사람이 컨트롤의 값을 변경할 때마다 발생합니다.  
  
### <a name="to-continue-or-review"></a>계속하거나 검토하려면  
  
- 퀴즈의 전체 버전을 다운로드하려면 [전체 수학 퀴즈 자습서 샘플](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c)을 참조하세요.  
  
- 다음 자습서로 이동하려면 [자습서 3: 일치 게임 만들기](../ide/tutorial-3-create-a-matching-game.md)합니다.  
  
- 이전 자습서 단계로 돌아가려면 [7단계: 곱하기 및 나누기 문제 추가](../ide/step-7-add-multiplication-and-division-problems.md)합니다.
