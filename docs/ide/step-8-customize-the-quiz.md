---
title: '8단계: 퀴즈 사용자 지정'
ms.custom: ''
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: conceptual
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09d020e2d83e7e631fefcb1503eb8f1938894986
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672121"
---
# <a name="step-8-customize-the-quiz"></a>8단계: 퀴즈 사용자 지정
자습서의 마지막 부분에서는 퀴즈를 사용자 지정하고 이미 배운 내용을 확장하는 몇 가지 방법을 살펴보겠습니다. 예를 들어 프로그램에서 답이 분수가 아닌 난수 나누기 문제를 만드는 방법을 생각해 보세요. 자세히 알아보려면 `timeLabel` 컨트롤을 다른 색으로 바꾸고 퀴즈를 푸는 사람에게 힌트를 제공합니다.  

## <a name="to-customize-the-quiz"></a>퀴즈를 사용자 지정하려면  

-   퀴즈에서 남은 시간이 5초뿐이라면 **BackColor** 속성(`timeLabel.BackColor = Color.Red;`)을 설정하여 **timeLabel** 컨트롤을 빨간색으로 바꿉니다. 퀴즈가 끝나면 색을 초기화합니다.  
  
-   <xref:System.Windows.Forms.NumericUpDown> 컨트롤에 정답이 입력되면 소리를 재생하여 퀴즈를 푸는 사람에게 힌트를 제공합니다. 각 컨트롤의 <xref:System.Windows.Forms.NumericUpDown.ValueChanged> 이벤트에 대한 이벤트 처리기를 작성해야 합니다. 이 이벤트는 퀴즈를 푸는 사람이 컨트롤의 값을 변경할 때마다 발생합니다.  
  
## <a name="to-continue-or-review"></a>계속하거나 검토하려면  
  
-   퀴즈의 전체 버전을 다운로드하려면 [Complete math quiz tutorial sample](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c)(전체 수학 퀴즈 자습서 샘플)을 참조하세요.  
  
-   다음 자습서로 이동하려면 [자습서 3: 일치 게임 만들기](../ide/tutorial-3-create-a-matching-game.md)를 참조하세요.  
  
-   이전 자습서 단계로 돌아가려면 [7단계: 곱하기 및 나누기 문제 추가](../ide/step-7-add-multiplication-and-division-problems.md)를 참조하세요.
