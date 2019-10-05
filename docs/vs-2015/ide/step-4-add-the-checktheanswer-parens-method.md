---
title: '4단계: Checktheanswer () 메서드 추가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a9806bad150a5d03a942c7dfb36753f91d10536e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442567"
---
# <a name="step-4-add-the-checktheanswer-method"></a>4단계: CheckTheAnswer() 메서드 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 자습서의 4단계에서는 수학 문제의 답이 맞는지 여부를 확인하는 `CheckTheAnswer()` 메서드를 작성합니다. 이 항목은 기본 코딩 개념에 대해 설명하는 자습서 시리즈의 일부입니다. 자습서에 대한 개요는 [자습서 2: 시간이 지정된 된 수학 퀴즈 만들기](../ide/tutorial-2-create-a-timed-math-quiz.md)합니다.  
  
> [!NOTE]
> 이 메서드는 값을 반환하기 때문에 Visual Basic 사용자는 일반적인 `Function` 키워드 대신 `Sub` 키워드를 사용합니다. 논리는 간단합니다. sub는 값을 반환하지 않고 function은 값을 반환합니다.  
  
### <a name="to-verify-whether-the-answers-are-correct"></a>답이 맞는지 여부를 확인하려면  
  
1. `CheckTheAnswer()` 메서드를 추가합니다.  
  
     이 메서드를 호출하면 addend1과 addend2의 값을 더하고 그 결과를 sum `NumericUpDown` 컨트롤의 값과 비교합니다. 두 값이 서로 같으면 이 메서드는 `true`를 반환하고 그렇지 않으면 `false`를 반환합니다. 이 코드는 다음과 같습니다.  
  
     [!code-csharp[VbExpressTutorial3Step4#8](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#8)]
     [!code-vb[VbExpressTutorial3Step4#8](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#8)]  
  
     다음으로 새 `CheckTheAnswer()` 메서드를 호출하도록 타이머의 Tick 이벤트 처리기에 대한 메서드에서 코드를 업데이트합니다.  
  
2. `if else` 문에 다음 코드를 추가합니다.  
  
     [!code-csharp[VbExpressTutorial3Step4#10](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step4/cs/form1.cs#10)]
     [!code-vb[VbExpressTutorial3Step4#10](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step4/vb/form1.vb#10)]  
  
     답이 맞으면 `CheckTheAnswer()`는 `true`를 반환합니다. 이벤트 처리기가 타이머를 중지하고 축하 메시지를 표시한 다음 **시작** 단추를 다시 사용할 수 있게 만듭니다. 답이 맞지 않으면 퀴즈를 계속합니다.  
  
3. 프로그램을 저장하고 실행합니다. 퀴즈를 시작하고 더하기 문제의 올바른 답을 입력합니다.  
  
    > [!NOTE]
    > 이때 답 입력을 시작하기 전에 기본값인 0을 선택하거나 수동으로 삭제해야 합니다. 이 동작은 이 자습서의 뒷부분에서 수정합니다.  
  
     올바른 답을 입력하면 메시지 상자가 열리고 **시작** 단추를 사용할 수 있게 되며 타이머가 중지됩니다.  
  
### <a name="to-continue-or-review"></a>계속하거나 검토하려면  
  
- 다음 자습서 단계로 이동하려면 [5단계: 추가 NumericUpDown 컨트롤에 대 한 Enter 이벤트 처리기](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)합니다.  
  
- 이전 자습서 단계로 돌아가려면 [3단계: 카운트다운 타이머 추가](../ide/step-3-add-a-countdown-timer.md)합니다.
