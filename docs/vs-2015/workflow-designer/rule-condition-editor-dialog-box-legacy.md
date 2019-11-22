---
title: Rule Condition Editor Dialog Box (Legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleConditionDialog.UI
helpviewer_keywords:
- Rule Condition dialog box
ms.assetid: c7ca8be9-de31-4a64-939c-4d53a50d5e29
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a632b90e89e58c26ec72083fe3f4ed9223826dae
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302852"
---
# <a name="rule-condition-editor-dialog-box-legacy"></a>규칙 조건 편집기 대화 상자(레거시)
This topic describes how use the **Rule Condition Editor** dialog box in the legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

 You create and modify declarative rule conditions by using the **Rule Condition Editor** dialog box. 이러한 규칙 조건은 기본적으로 제공되는 다음과 같은 Windows Workflow Foundation 활동에 대한 속성으로 나타납니다.

- [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017)

- [IfElseBranchActivity](https://go.microsoft.com/fwlink?LinkID=65034)

- [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039)

- [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049)

- [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040)

- [StateMachineWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65045)

  You access the **Rule Condition Editor** dialog box by using the [Select Condition Dialog Box (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).

  The following table describes the user interface (UI) elements of the **Rule Condition Editor** dialog box.

|UI 요소|설명|
|----------------|-----------------|
|**Condition:**|규칙 조건을 위한 식을 입력합니다.|
|**OK**|규칙 조건을 저장하려면 클릭합니다.|

## <a name="entering-condition-expressions"></a>조건식 입력
 조건식은 텍스트로 입력합니다. You can type **this.** into the editor to reference fields, properties, and methods used in the workflow, using an IntelliSense-like menu. 또는 워크플로 멤버 이름을 직접 입력할 수도 있습니다. AND, OR, NOT 등의 논리 연산자를 조건에 추가할 수 있습니다. 조건자를 추가할 수도 있습니다. 조건자는 이항 연산자 한 개와 피연산자 두 개로 이루어집니다. The binary operators supported are **==** , **>** , **\<** , **>=** , and **<=** . 지원되는 피연산자는 상수 값, 산술 함수 및 범위 Public 멤버입니다.

 You can specify the type for the comparison, and you can compare to **null** or an empty string. `this.Address.State == "WA"`와 같이 복합 형식을 포함하는 변수에서 멤버에 대한 중첩 호출을 수행할 수 있습니다.

 규칙 조건 편집기는 다음과 같은 연산자를 지원합니다.

- 관계형 연산자: ==, =, !=

- Comparison operators: <, \<=, >, >=

- 산술 연산자: +, - , *, /, MOD

- Logical operators: AND, &&, OR, &#124;&#124;, NOT, !

- Bitwise operators: &, &#124;

  식 연산자 우선 순위는 C# 연산자 우선 순위 규칙을 따릅니다.

  규칙 조건 편집기는 다음과 같은 숫자 식을 지원합니다.

  this.i == 1D(1.0으로 해석됨)

  this.i == 1E1(10.0으로 해석됨)

  this.i == 1L(long 형식으로 해석됨)

  this.i == 1M(10진수로 해석됨)

  this.i == 1F(single 형식으로 해석됨)

  this.i == 1U(unsigned int 형식으로 해석됨)

  For more information about conditions, see [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009).

## <a name="see-also"></a>관련 항목:
 [IfElseActivity](https://go.microsoft.com/fwlink?LinkID=65033) [ConditionedActivityGroup](https://go.microsoft.com/fwlink?LinkID=65017) [ReplicatorActivity](https://go.microsoft.com/fwlink?LinkID=65039) [WhileActivity](https://go.microsoft.com/fwlink?LinkID=65049) [Select Condition Dialog Box (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md) [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009) [Legacy Designer for Windows Workflow Foundation UI Help](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)