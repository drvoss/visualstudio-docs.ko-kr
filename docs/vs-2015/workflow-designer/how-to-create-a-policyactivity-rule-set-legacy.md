---
title: 'How to: Create a PolicyActivity Rule Set (Legacy) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c18a08986bf8e4aa30969a9d30d740fb68e978c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297470"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>방법: PolicyActivity 규칙 집합 만들기(레거시)
이 항목에서는 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 또는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 대상으로 하는 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 사용하여 정책 활동 규칙 집합을 만드는 방법에 대해 설명합니다.

 After you have dragged a **Policy** activity item from the **Toolbox** to the workflow design surface, you will want to select an existing rule or create a new rule set for the [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) activity. You select an existing rule set by using the [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) and you create rule sets by using the [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> You can open the [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) dialog box directly by double-clicking on a [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) activity that is on the workflow design surface.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>PolicyActivity 활동의 규칙 집합을 선택하거나 만들려면

1. Right-click the [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019), and then click **Properties** to open the **Properties** window.

2. Click the **RuleSetReference** property.

3. 다음 작업 중 하나를 수행합니다.

    - Click the **RuleSetReference** ellipses **[…]** , and then select an existing rule set in the [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md). 10단계로 이동합니다.

         또는

    - 규칙 집합의 이름을 입력합니다. Click the **RuleSetReference** ellipses **[…]** , and then select **Edit** in the [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         또는

    - 규칙 집합의 이름을 입력합니다. Expand the **RuleSetReference** property and select the ellipses **[…]** in the **RuleSet Definition** property.

         The [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) opens.

4. In the [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), click **Add Rule** to add a new rule to the rule set.

5. Enter the **Name**, **Priority**, and **Reevaluation** properties, or keep the default values.

6. Enter the text for the **Condition**.

7. Enter the text for the **Then Actions** and the **Else Actions**.

8. Click **Add Rule** again to add another rule.

9. 작업을 마쳤으면 **확인**을 클릭합니다.

## <a name="see-also"></a>관련 항목:
 [PolicyActivity](https://go.microsoft.com/fwlink?LinkID=65019) [Select Rule Set Dialog Box (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [Rule Set Editor Dialog Box (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) [Using the Policy Activity](https://go.microsoft.com/fwlink?LinkID=65004) [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md)