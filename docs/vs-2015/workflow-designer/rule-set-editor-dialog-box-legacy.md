---
title: 규칙 집합 편집기 대화 상자 (레거시) | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 862842bd41762b15a38254c9d5e21bf06cdca10a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703201"
---
# <a name="rule-set-editor-dialog-box-legacy"></a>규칙 집합 편집기 대화 상자(레거시)
에 대해 설명 하는 방법을 사용 하 여는 **규칙 집합 편집기** 레거시 대화 상자 [!INCLUDE[wfd1](../includes/wfd1-md.md)]합니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.  
  
 합니다 **규칙 집합 편집기** 대화 상자는 만들기 및 수정 하는 데 사용 됩니다 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) 규칙 집합을.rules 파일로 serialize 됩니다.  
  
> [!NOTE]
> 사용 하 여.rules 파일을 열려고 할 경우는 **인코딩을 사용 하 여 XML 편집기**를 워크플로 또는 활동에 대 한 연결된 된 디자이너 창을 닫아야 합니다.  
  
 액세스 하는 방법에 대 한 자세한 합니다 **규칙 집합 편집기** 대화 상자, 참조 [방법: PolicyActivity 규칙 집합 만들기 (레거시)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md)합니다.  
  
> [!WARNING]
> [!INCLUDE[wfd2](../includes/wfd2-md.md)] 또는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 대상으로 하는 데 사용되는 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]의 규칙 편집기는 멀티 타게팅을 지원하지 않습니다.  
  
 다음 표에 사용자 인터페이스 (UI) 요소에는 **규칙 집합 편집기** 대화 상자.  
  
|UI 요소|설명|  
|----------------|-----------------|  
|**규칙 추가**|규칙 집합에 새 규칙 정의를 추가합니다.|  
|**삭제**|선택한 규칙을 규칙 집합에서 삭제합니다.|  
|**체 이닝**|규칙 집합에 사용할 전방 연결의 형식을 지정합니다. 사용 가능한 옵션은 다음과 같습니다.<br /><br /> -   **전체 연결**, 모든 전방 연결 메커니즘을 사용 하도록 지정 하는: 암시적, 메서드 특성 지정 하 고 명시적으로 사용 하는 **업데이트** 함수입니다.<br />-   **순차**, 전방 연결을 사용 하지 않도록 지정 하는 합니다.<br />-   **명시적 업데이트만**에에서 전방 연결을 수행 하도록 지정 하는 **업데이트** 작업 합니다.<br /><br /> 전방 연결에 대 한 자세한 내용은 참조 하세요. [PolicyActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65004)입니다.|  
|**이름**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 이름별로 정렬하려면 클릭합니다.|  
|**Priority**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 우선 순위별로 정렬하려면 클릭합니다.|  
|**재평가**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 재계산 형식별로 정렬하려면 클릭합니다.|  
|**규칙 미리 보기**|규칙 집합 목록 열 머리글입니다. 규칙 목록을 규칙의 조건 및 작업 미리 보기별로 정렬하려면 클릭합니다.|  
|**이름:**|규칙의 이름을 입력합니다.|  
|**우선 순위:**|규칙의 우선 순위를 입력합니다. 기본 우선 순위는 0입니다.|  
|**재평가 합니다.**|규칙에 사용할 규칙 재계산의 형식을 지정합니다. 사용 가능한 옵션은 다음과 같습니다.<br /><br /> -   **항상**, 필요에 따라 다시 평가 규칙에 이르게 합니다.<br />-   **되지**, 그러면 규칙을 재계산 하지 않습니다. 이 경우에는 규칙이 한 번만 실행됩니다.|  
|**활성**|규칙을 활성화하려면 선택합니다.|  
|**조건:**|규칙 조건을 위한 식을 입력합니다. 식 구문에 대한 자세한 내용은 이 페이지의 "조건 및 작업 식 입력" 단원을 참조하세요.|  
|**Thenactions:**|Then 작업을 위한 식을 입력합니다. 식 구문에 대한 자세한 내용은 이 페이지의 "조건 및 작업 식 입력" 단원을 참조하세요.|  
|**Else 작업:**|Else 작업을 위한 식을 입력합니다. 식 구문에 대한 자세한 내용은 이 페이지의 "조건 및 작업 식 입력" 단원을 참조하세요.|  
|**확인**|규칙 집합을 .rules 파일로 저장하려면 클릭합니다.|  
  
 규칙 집합에 대 한 자세한 내용은 참조 하세요. [PolicyActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65004)입니다.  
  
## <a name="entering-condition-and-action-expressions"></a>조건 및 작업 식 입력  
 조건 및 Then 식을 입력 하 고 다른 작업 각 텍스트에서는 텍스트 상자에 **규칙 집합 편집기** 대화 상자. 입력할 수 있습니다 **이 있습니다.** 참조 필드, 속성 및 워크플로에서 사용 되는 메서드를 편집기에는 IntelliSense 형식의 메뉴를 사용 합니다. 또는 워크플로 멤버 이름을 직접 입력할 수도 있습니다. 클래스 이름 다음에 메서드 이름을 입력하여 정적 메서드를 참조 형식으로 호출할 수 있습니다.  
  
 AND, OR, NOT 등의 논리 연산자를 조건에 추가할 수 있습니다. 조건자를 추가할 수도 있습니다. 조건자는 이항 연산자 한 개와 피연산자 두 개로 이루어집니다. 지원 되는 이항 연산자는 = =, >, \<, > = 및 < =입니다. 지원되는 피연산자는 상수 값, 산술 함수 및 범위 Public 멤버입니다.  
  
 비교 유형을 지정할 수 있습니다 및 비교할 수 있습니다 **null** 또는 빈 문자열입니다. `this.Address.State == "WA"`와 같이 복합 형식을 포함하는 변수에서 멤버 호출을 중첩시킬 수 있습니다.  
  
 식은 다음과 같은 연산자를 지원합니다.  
  
- 관계형 연산자: ==, =, !=  
  
- 비교 연산자: <, \<=, >, > =  
  
- 산술 연산자: +, - , *, /, MOD  
  
- 논리 연산자 AND, &&, OR, &#124;&#124;, NOT, !  
  
- 비트 연산자: &,&#124;  
  
  식 연산자 우선 순위는 C# 연산자 우선 순위 규칙을 따릅니다.  
  
  조건에 대 한 자세한 내용은 참조 하세요. [워크플로에서 조건 사용](https://msdn.microsoft.com/541211f5-d382-4810-894f-71f00b34fa77)합니다.  
  
### <a name="halt-and-update-functions"></a>Halt 및 Update 함수  
 **Thenactions:** 하 고 **Else 작업:** 식은 지원 **중단** 하 고 **업데이트** 함수. 사용 하는 **중단** 함수를 입력 **중단** 에 **Thenaction:** 또는 **Else 작업:** 입력란. 합니다 **중단** 작업 규칙 집합 실행이 즉시 중지 시키고 호출 코드로 컨트롤을 반환 합니다. 사용 된 **업데이트** 전방 연결과 함께 함수입니다.  
  
 **업데이트** 두 형식 중 하나로 편집기에서 문을 표현할 수 있습니다; 그리고 두 형태 모두 다음 예제에 표시 됩니다.  
  
```  
Update(this.Address.State)  
Update("this/Address/State")  
```  
  
 사용에 대 한 자세한 내용은 **업데이트** 전방 연결과 함께 참조 [PolicyActivity 활동을 사용 하 여](http://go.microsoft.com/fwlink?LinkID=65004)입니다.  
  
## <a name="see-also"></a>참고 항목  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [규칙 집합 선택 대화 상자 (레거시)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [PolicyActivity 활동 사용](http://go.microsoft.com/fwlink?LinkID=65004)   
 [워크플로에서 조건 사용](http://go.microsoft.com/fwlink?LinkID=65009)