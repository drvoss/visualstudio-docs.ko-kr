---
title: '방법: PolicyActivity 규칙 집합 만들기 (레거시) | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bf1fd84d884068d11d15d614f5e281577bd3ce55
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433578"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>방법: PolicyActivity 규칙 집합 만들기(레거시)
이 항목에서는 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 또는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 대상으로 하는 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 사용하여 정책 활동 규칙 집합을 만드는 방법에 대해 설명합니다.  
  
 끌어 온 후는 **정책** 에서 작업 항목은 **도구 상자** 워크플로 디자인 화면에 하려는 새 규칙 집합을 만들거나 기존 규칙을 선택 합니다 [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) 활동입니다. 사용 하 여 설정 하는 기존 규칙을 선택 합니다 [선택 규칙 설정 대화 상자 (레거시)](../workflow-designer/select-rule-set-dialog-box-legacy.md) 사용 하 여 규칙 집합을 만듭니다는 [규칙 집합 편집기 대화 상자 (레거시)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)합니다.  
  
> [!NOTE]
> 열 수 있습니다 합니다 [규칙 집합 편집기 대화 상자 (레거시)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) 을 두 번 클릭 하 여 직접 대화 상자를 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) 워크플로 디자인 화면에 있는 작업입니다.  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>PolicyActivity 활동의 규칙 집합을 선택하거나 만들려면  
  
1. 마우스 오른쪽 단추로 클릭 합니다 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), 클릭 하 고 **속성** 열려는 합니다 **속성** 창.  
  
2. 클릭 합니다 **RuleSetReference** 속성입니다.  
  
3. 다음 작업 중 하나를 수행합니다.  
  
    - 클릭 합니다 **RuleSetReference** 줄임표 **[...]** 를 선택한 다음 기존 규칙에서 설정 합니다 [선택 규칙 설정 대화 상자 (레거시)](../workflow-designer/select-rule-set-dialog-box-legacy.md)합니다. 10단계로 이동합니다.  
  
         또는  
  
    - 규칙 집합의 이름을 입력합니다. 클릭 합니다 **RuleSetReference** 줄임표 **[...]** 를 선택한 후 **편집** 에 [선택 규칙 설정 대화 상자 (레거시)](../workflow-designer/select-rule-set-dialog-box-legacy.md)합니다.  
  
         또는  
  
    - 규칙 집합의 이름을 입력합니다. 확장 된 **RuleSetReference** 속성과 줄임표 선택 **[...]**  에 **RuleSet Definition** 속성입니다.  
  
         합니다 [규칙 집합 편집기 대화 상자 (레거시)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) 열립니다.  
  
4. 에 [규칙 집합 편집기 대화 상자 (레거시)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), 클릭 **규칙 추가** 규칙 집합에 새 규칙을 추가 하려면.  
  
5. 입력를 **이름**, **우선 순위**, 및 **재평가** 속성 또는 기본값을 그대로 유지 합니다.  
  
6. 에 텍스트를 입력 합니다 **조건을**합니다.  
  
7. 에 텍스트를 입력 합니다 **Thenactions** 하며 **Else 작업**합니다.  
  
8. 클릭 **규칙 추가** 다른 규칙을 추가 하려면 다시 합니다.  
  
9. 작업을 마쳤으면 **확인**을 클릭합니다.  
  
## <a name="see-also"></a>참고 항목  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [규칙 집합 선택 대화 상자 (레거시)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [규칙 집합 편집기 대화 상자 (레거시)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Policyactivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65004)   
 [레거시 워크플로 활동](../workflow-designer/legacy-workflow-activities.md)