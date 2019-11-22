---
title: Rule Set Editor Dialog Box (Legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.Activities.Rules.Design.RuleSetDialog.UI
helpviewer_keywords:
- Rule Set Editor dialog box
ms.assetid: 7cfd5df1-1115-4e5c-9b72-121f39419e83
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83cdd4f549655be524abdd2a4708b316f6747b3e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302762"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>규칙 집합 편집기 대화 상자(레거시)
This topic describes how use the **Rule Set Editor** dialog box in the legacy [!INCLUDE[wfd1](../includes/wfd1-md.md)]. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

 The **Rule Set Editor** dialog box is used to create and modify [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) rule sets, which are serialized to a .rules file.

> [!NOTE]
> If you want to open the .rules file with the **XML Editor with encoding**, you must first close the associated designer window for the workflow or activity.

 For information about how to access the **Rule Set Editor** dialog box, see [How to: Create a PolicyActivity Rule Set (Legacy)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md).

> [!WARNING]
> [!INCLUDE[wfd2](../includes/wfd2-md.md)] 또는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 대상으로 하는 데 사용되는 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]의 규칙 편집기는 멀티 타게팅을 지원하지 않습니다.

 The following table describes the user interface (UI) elements of the **Rule Set Editor** dialog box.

|UI 요소|설명|
|----------------|-----------------|
|**Add Rule**|규칙 집합에 새 규칙 정의를 추가합니다.|
|**삭제**|선택한 규칙을 규칙 집합에서 삭제합니다.|
|**Chaining**|규칙 집합에 사용할 전방 연결의 형식을 지정합니다. 사용 가능한 옵션은 다음과 같습니다.<br /><br /> -   **Full Chaining**, which specifies to use all forward chaining mechanisms: implicit, method attributing, and explicit using an **Update** function.<br />-   **Sequential**, which specifies not to use any forward chaining.<br />-   **Explicit Update Only**, which specifies to only perform forward chaining on **Update** actions.<br /><br /> For more information about forward chaining, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).|
|**이름**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 이름별로 정렬하려면 클릭합니다.|
|**Priority**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 우선 순위별로 정렬하려면 클릭합니다.|
|**Reevaluation**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 재계산 형식별로 정렬하려면 클릭합니다.|
|**Rule Preview**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 규칙의 조건 및 작업 미리 보기별로 정렬하려면 클릭합니다.|
|**Name:**|규칙의 이름을 입력합니다.|
|**Priority:**|규칙의 우선 순위를 입력합니다. 기본 우선 순위는 0입니다.|
|**Reevaluation:**|규칙에 사용할 규칙 재계산의 형식을 지정합니다. 사용 가능한 옵션은 다음과 같습니다.<br /><br /> -   **Always**, which causes the rule to be reevaluated as needed.<br />-   **Never**, which causes the rule to never be reevaluated. 이 경우에는 규칙이 한 번만 실행됩니다.|
|**활성**|규칙을 활성화하려면 선택합니다.|
|**Condition:**|규칙 조건을 위한 식을 입력합니다. 식 구문에 대한 자세한 내용은 이 페이지의 "조건 및 작업 식 입력" 단원을 참조하세요.|
|**Then Actions:**|Then 작업을 위한 식을 입력합니다. 식 구문에 대한 자세한 내용은 이 페이지의 "조건 및 작업 식 입력" 단원을 참조하세요.|
|**Else Actions:**|Else 작업을 위한 식을 입력합니다. 식 구문에 대한 자세한 내용은 이 페이지의 "조건 및 작업 식 입력" 단원을 참조하세요.|
|**OK**|규칙 집합을 .rules 파일로 저장하려면 클릭합니다.|

 For more information about rule sets, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).

## <a name="entering-condition-and-action-expressions"></a>조건 및 작업 식 입력
 You enter expressions for the Condition and the Then and Else actions as text in their respective text boxes in the **Rule Set Editor** dialog box. You can type **this.** into the editor to reference fields, properties and methods used in the workflow, using an IntelliSense-type of menu. 또는 워크플로 멤버 이름을 직접 입력할 수도 있습니다. 클래스 이름 다음에 메서드 이름을 입력하여 정적 메서드를 참조 형식으로 호출할 수 있습니다.

 AND, OR, NOT 등의 논리 연산자를 조건에 추가할 수 있습니다. 조건자를 추가할 수도 있습니다. 조건자는 이항 연산자 한 개와 피연산자 두 개로 이루어집니다. The binary operators supported are ==, >, \<, >=, and <=. 지원되는 피연산자는 상수 값, 산술 함수 및 범위 Public 멤버입니다.

 You can specify the type for the comparison, and you can compare to **null** or an empty string. `this.Address.State == "WA"`와 같이 복합 형식을 포함하는 변수에서 멤버 호출을 중첩시킬 수 있습니다.

 식은 다음과 같은 연산자를 지원합니다.

- 관계형 연산자: ==, =, !=

- Comparison operators: <, \<=, >, >=

- 산술 연산자: +, - , *, /, MOD

- Logical operators: AND, &&, OR, &#124;&#124;, NOT, !

- Bitwise operators: &, &#124;

  식 연산자 우선 순위는 C# 연산자 우선 순위 규칙을 따릅니다.

  For more information about conditions, see [Using Conditions in Workflows](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77).

### <a name="halt-and-update-functions"></a>Halt 및 Update 함수
 **Then Actions:** and **Else Actions:** expressions support **Halt** and **Update** functions. To use the **Halt** function, type **Halt** into a **Then Action:** or **Else Action:** text box. The **Halt** action causes rule set execution to stop immediately, and control returns to the calling code. You use the **Update** function with forward chaining.

 An **Update** statement can be expressed in the editor in one of two forms; both forms are shown in the following example:

```
Update(this.Address.State)
Update("this/Address/State")
```

 For more information about using **Update** with forward chaining, see [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004).

## <a name="see-also"></a>관련 항목:
 [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [Using the PolicyActivity Activity](https://go.microsoft.com/fwlink?LinkID=65004) [Using Conditions in Workflows](https://go.microsoft.com/fwlink?LinkID=65009)