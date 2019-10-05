---
title: '방법: 선언적 규칙 조건 만들기 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dbdcc268b71f2926307b500126840391dd5308fd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931239"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>방법: 선언적 규칙 조건 만들기(레거시)
이 항목에서는 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 또는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 대상으로 하는 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 사용하여 규칙 조건을 선언하는 방법에 대해 설명합니다.  
  
 계산 되는 조건문 **True** 하거나 **False**합니다. 선언적 규칙 조건을 사용 하 여 만든는 조건문은는 [규칙 조건 편집기 대화 상자 (레거시)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) 워크플로 사용 하 여 XML로 저장 합니다. 여러 조건자를 결합하는 부울 대수와 워크플로 상태를 비교하는 조건자가 포함될 수 있습니다.  
  
 선언적 규칙 조건은 기본적으로 제공되는 다음과 같은 Windows Workflow Foundation 활동에 사용됩니다.  
  
- [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
- [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
- [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
- [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
- [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
- [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>규칙 조건 편집기를 사용하여 선언적 규칙 조건을 만들려면  
  
1. 활동에서 **속성** 창 클릭 합니다 **조건** 속성 또는 **UntilCondition** activity에 따라 속성입니다.  
  
2. 선택 **선언적 규칙 조건** 속성 목록에서.  
  
3. 확장을 **조건을** 하거나 **UntilCondition** 속성입니다.  
  
4. 클릭 합니다 **ConditionName** 속성입니다.  
  
5. 클릭 합니다 **ConditionName** 줄임표 **[...]**  열려면 합니다 **조건 선택** 대화 상자.  
  
6. 클릭 **새 조건** 열려는 합니다 **Rule Condition Editor** 대화 상자.  
  
7. 조건에 식을 입력 합니다 **조건을** 입력란입니다.  
  
     조건식을 만드는 방법에 대 한 자세한 내용은 [규칙 조건 편집기 대화 상자 (레거시)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)합니다.  
  
8. 조건 식 만들기 완료 되 면 **확인** 를 대화 상자를 닫고 할당 된 이름으로 규칙 조건을 만듭니다.  
  
     합니다 **조건 선택** 대화 상자가 열립니다.  
  
     사용 하는 방법에 대 한 자세한 합니다 **조건 선택** 대화 상자, 참조 [조건 선택 대화 상자 (레거시)](../workflow-designer/select-condition-dialog-box-legacy.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 워크플로 활동](../workflow-designer/legacy-workflow-activities.md)   
 [Conditionedactivitygroup 활동 사용](http://go.microsoft.com/fwlink?LinkID=65066)   
 [IfElseBranchActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Replicatoractivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65080)   
 [While을 사용 하 여 활동](http://go.microsoft.com/fwlink?LinkID=65091)   
 [규칙 조건 편집기 대화 상자 (레거시)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [조건 선택 대화 상자 (레거시)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [워크플로에서 조건 사용](http://go.microsoft.com/fwlink?LinkID=65009)