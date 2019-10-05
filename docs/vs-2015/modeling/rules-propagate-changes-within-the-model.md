---
title: 규칙에는 모델 내부의 변경 내용 전파 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
ms.assetid: 1690a38a-c8f5-4bc6-aab9-015771ec6647
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 29950be152c140a8315f96f8752b1fa906c3f801
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442937"
---
# <a name="rules-propagate-changes-within-the-model"></a>규칙으로 모델 내부의 변경 내용 전파
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visualization and Modeling SDK (VMSDK)에서 다른 요소에서 변경 전파 하는 저장소 규칙을 만들 수 있습니다. 저장소의 모든 요소에는 변경이 발생 하는 경우 규칙은 가장 바깥쪽 트랜잭션이 커밋될 때 일반적으로 실행할 예약 됩니다. 다른 유형의 여러 가지 요소를 추가 또는 삭제와 같은 이벤트에 대 한 규칙이 있습니다. 요소, 모양 또는 다이어그램의 특정 형식에 규칙을 연결할 수 있습니다. 많은 기본 제공 기능 규칙에 의해 정의 됩니다: 다이어그램 모델 변경 될 때 업데이트 되는 규칙을 확인 하는 예를 들어, 합니다. 사용자 고유의 규칙을 추가 하 여 도메인 특정 언어를 사용자 지정할 수 있습니다.  

 저장소 규칙 저장소-즉, 내부 변경 내용 전파 변경 내용을 모델 요소, 관계, 모양 또는 커넥터 및 해당 도메인 속성에 특히 유용 합니다. 사용자는 실행 취소 또는 다시 실행 명령을 호출 하는 경우 규칙이 실행 되지 않습니다. 대신 트랜잭션 관리자 저장소 콘텐츠는 올바른 상태로 복원할 수 있습니다. Store 외부의 리소스에 대 한 변경 내용을 전파 하려는 경우 이벤트 저장을 사용 합니다. 자세한 내용은 [이벤트 처리기 전파 변경 외부 모델](../modeling/event-handlers-propagate-changes-outside-the-model.md)합니다.  

 예를 들어, 사용자 (또는 코드) ExampleDomainClass 형식의 새 요소를 만들 때마다 다른 형식의 추가 요소가 만들어지도록 지정할 모델의 다른 부분에 한다고 가정 합니다. AddRule를 작성 하 고 ExampleDomainClass에 연결할 수 없습니다. 추가 요소를 만드는 규칙에서 코드를 작성 합니다.  

```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using Microsoft.VisualStudio.Modeling;  

namespace ExampleNamespace  
{  
 // Attribute associates the rule with a domain class:  
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]  
 // The rule is a class derived from one of the abstract rules:  
 class MyAddRule : AddRule  
 {  
  // Override the abstract method:  
  public override void ElementAdded(ElementAddedEventArgs e)  
  {  
    base.ElementAdded(e);  
    ExampleDomainClass element = e.ModelElement;  
    Store store = element.Store;  
    // Ignore this call if we're currently loading a model:  
    if (store.TransactionManager.CurrentTransaction.IsSerializing)   
       return;  

    // Code here propagates change as required – for example:  
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);  
      echo.Name = element.Name;  
      echo.Parent = element.Parent;    
    }  
  }  
 // The rule must be registered:  
 public partial class ExampleDomainModel  
 {  
   protected override Type[] GetCustomDomainModelTypes()  
   {  
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
     types.Add(typeof(MyAddRule));  
     // If you add more rules, list them here.   
     return types.ToArray();  
   }  
 }  
}  

```  

> [!NOTE]
> 규칙의 코드는 저장소 내에서 요소의 상태를 변경 해야 즉, 모델 요소, 관계, 모양, 연결선, 다이어그램 또는 해당 속성만 규칙을 변경 해야 합니다. Store 외부의 리소스에 대 한 변경 내용을 전파 하려는 경우 저장소 이벤트를 정의 합니다. 자세한 내용은 참조 하세요. [이벤트 처리기 전파 변경 외부 모델](../modeling/event-handlers-propagate-changes-outside-the-model.md)  

### <a name="to-define-a-rule"></a>규칙을 정의 하려면  

1. 클래스 접두사로 규칙 정의 `RuleOn` 특성입니다. 특성에 도메인 클래스, 관계 또는 다이어그램 요소 중 하나를 사용 하 여 규칙을 연결합니다. 규칙은 추상 일 수 있는이 클래스의 모든 인스턴스에 적용 됩니다.  

2. 규칙에서 반환 된 집합에 추가 하 여 등록 `GetCustomDomainModelTypes()` 도메인 모델 클래스입니다.  

3. 규칙 클래스는 추상 규칙 클래스 중 하나에서 파생 하 고 실행 메서드에 코드를 작성 합니다.  

   다음 섹션에서는 이러한 단계를 자세히 설명합니다.  

### <a name="to-define-a-rule-on-a-domain-class"></a>도메인 클래스에 규칙을 정의 하려면  

- 사용자 지정 코드 파일에서 클래스를 정의 하 고 사용 하 여 접두사를 <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> 특성:  

    ```  
    [RuleOn(typeof(ExampleElement),   
         // Usual value – but required, because it is not the default:  
         FireTime = TimeToFire.TopLevelCommit)]   
    class MyRule ...  

    ```  

- 첫 번째 매개 변수 형식을 주체 도메인 클래스, 도메인 관계, 모양, 연결선 또는 다이어그램 수 있습니다. 일반적으로 도메인 클래스 및 관계에 규칙을 적용 합니다.  

     합니다 `FireTime` 일반적으로 `TopLevelCommit`입니다. 이렇게 하면 트랜잭션의 모든 기본 변경 내용을 적용 된 후에 규칙이 실행 되도록 합니다. 대체는 규칙 변경; 즉시 실행 하는 인라인 및 LocalCommit (가장 바깥쪽 일 수 있음)는 현재 트랜잭션이 끝날 때 규칙을 실행 합니다. 큐에서 순서에 영향을 하는 규칙의 우선 순위를 설정할 수도 있습니다 이지만 필요한 결과 달성 하는 불안정 한 메서드를 합니다.  

- 주체 유형으로 추상 클래스를 지정할 수 있습니다.  

- 규칙 제목 클래스의 모든 인스턴스에 적용 됩니다.  

- 에 대 한 기본값 `FireTime` TimeToFire.TopLevelCommit 됩니다. 이렇게 하면 가장 바깥쪽 트랜잭션이 커밋될 때 실행할 규칙. 대안은 TimeToFire.Inline 합니다. 그러면 규칙 트리거 이벤트 직후 실행 될 수 있습니다.  

### <a name="to-register-the-rule"></a>규칙을 등록 하려면  

- 규칙 클래스에 의해 반환 된 형식 목록에 추가 `GetCustomDomainModelTypes` 도메인 모델에서:  

    ```  
    public partial class ExampleDomainModel  
     {  
       protected override Type[] GetCustomDomainModelTypes()  
       {  
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
         types.Add(typeof(MyAddRule));  
         // If you add more rules, list them here.   
         return types.ToArray();  
       }  
     }  

    ```  

- 도메인 모델 클래스의 이름을 모르는 경우 파일을 자세히 살펴보고 **Dsl\GeneratedCode\DomainModel.cs**  

- DSL 프로젝트의 사용자 지정 코드 파일에서이 코드를 작성 합니다.  

### <a name="to-write-the-code-of-the-rule"></a>규칙의 코드를 작성 하려면  

- 규칙 클래스는 다음 기본 클래스 중 하나에서 파생 됩니다.  

  |                             기본 클래스                              |                                                                                                                                                                                                                                                                                                                                                                              트리거                                                                                                                                                                                                                                                                                                                                                                              |
  |---------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |           <xref:Microsoft.VisualStudio.Modeling.AddRule>            |                                                                                                                                                                                                                                                                                                                        요소, 링크 또는 셰이프 추가 됩니다.<br /><br /> 이 사용 하 여 새 요소 외에도 새 관계를 검색 합니다.                                                                                                                                                                                                                                                                                                                        |
  |          <xref:Microsoft.VisualStudio.Modeling.ChangeRule>          | 도메인 속성 값을 변경 됩니다. 메서드 인수는 이전 및 새 값을 제공합니다.<br /><br /> 모양의 경우이 규칙이 트리거된 경우 기본 제공 `AbsoluteBounds` 모양을 이동 되 면 속성 변경 합니다.<br /><br /> 대부분의 경우에서 재정의 하는 편리한 것 `OnValueChanged` 또는 `OnValueChanging` 속성 처리기에서 합니다. 이러한 메서드는 직전 및 변경 된 후 호출 됩니다. 반면 규칙은 일반적으로 트랜잭션이 끝날 때 실행 됩니다. 자세한 내용은 [도메인 속성 값 변경 처리기](../modeling/domain-property-value-change-handlers.md)합니다. **참고:**  이 규칙은 링크를 만들거나 삭제 하는 경우에 트리거되지 않습니다. 대신 작성 한 `AddRule` 및 `DeleteRule` 도메인 관계에 대 한 합니다. |
  |         <xref:Microsoft.VisualStudio.Modeling.DeletingRule>         |                                                                                                                                                                                                                                                                                                             요소 또는 링크를 삭제할 경우에 트리거됩니다. ModelElement.IsDeleting 속성은 트랜잭션이 끝날 때까지 true.                                                                                                                                                                                                                                                                                                              |
  |          <xref:Microsoft.VisualStudio.Modeling.DeleteRule>          |                                                                                                                                                                                                       요소 또는 링크 삭제 되었을 때 수행 됩니다. 다른 모든 규칙 실행 한 후, DeletingRules를 포함 하 여 규칙이 실행 됩니다. ModelElement.IsDeleting false 이며 ModelElement.IsDeleted 그렇습니다. 이후 실행 취소를 허용 하려면 요소가 제거 되지 않습니다 실제로 메모리에서 있지만 Store.ElementDirectory에서 제거 됩니다.                                                                                                                                                                                                       |
  |           <xref:Microsoft.VisualStudio.Modeling.MoveRule>           |                                                                                                                                                                                                                                                                                                           요소는 다른 하나의 저장소 파티션에서 이동 됩니다.<br /><br /> (고 지는이 관련이 없는 모양의 그래픽 위치)입니다.                                                                                                                                                                                                                                                                                                            |
  |     <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule>     |                                                                                                                                                                                                                                                                                                                 도메인 관계에만이 규칙이 적용 됩니다. 링크의 양쪽 끝에 모델 요소를 명시적으로 할당 하는 경우 트리거됩니다.                                                                                                                                                                                                                                                                                                                 |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> |                                                                                                                                                                                                                                                                                                                   요소와 링크의 순서가 MoveBefore 또는 MoveToIndex 메서드를 사용 하 여 링크 변경 될 때 트리거됩니다.                                                                                                                                                                                                                                                                                                                    |
  |   <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule>   |                                                                                                                                                                                                                                                                                                                                                              트랜잭션을 만들 때 실행 합니다.                                                                                                                                                                                                                                                                                                                                                              |
  |  <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule>   |                                                                                                                                                                                                                                                                                                                                                      트랜잭션이 커밋할 수 되려고 할 때 실행 합니다.                                                                                                                                                                                                                                                                                                                                                      |
  |  <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule>  |                                                                                                                                                                                                                                                                                                                                                     트랜잭션을 롤백할 수 되려고 할 때 실행 합니다.                                                                                                                                                                                                                                                                                                                                                     |

- 각 클래스에 메서드를 재정의 합니다. 형식 `override` 에서 클래스를 검색 합니다. 이 메서드의 매개 변수에 변경 되는 요소를 식별 합니다.  

  규칙에 대 한 다음 사항에 유의 합니다.  

1. 트랜잭션에서 변경 집합이 여러 규칙을 트리거할 수 있습니다. 일반적으로 규칙은 가장 바깥쪽 트랜잭션이 커밋될 때 실행 됩니다. 지정 되지 않은 순서로 실행 됩니다.  

2. 규칙은 항상 트랜잭션 내에서 실행 됩니다. 따라서 변경 하려면 새 트랜잭션을 만들 필요가 없습니다.  

3. 트랜잭션이 롤백될 때, 또는 실행 취소 또는 다시 실행 작업을 수행할 때 규칙 실행 되지 않습니다. 이러한 작업 저장소의 모든 내용이 이전 상태로 다시 설정 합니다. 따라서 경우 스토어 외부에 있는 항목의 상태를 변경 하는 규칙을이 수 하지 기억 synchronism 저장소와 콘텐츠. Store 외부의 상태를 업데이트 하려면 이벤트를 사용 하는 것이 좋습니다. 자세한 내용은 [이벤트 처리기 전파 변경 외부 모델](../modeling/event-handlers-propagate-changes-outside-the-model.md)합니다.  

4. 모델 파일에서 로드 되 면 몇 가지 규칙이 실행 됩니다. 로드 하거나 저장 진행에서 중인지 여부를 확인 하려면 `store.TransactionManager.CurrentTransaction.IsSerializing`합니다.  

5. 규칙의 코드를 추가 규칙 트리거를 만드는 경우 실행 목록 끝에 추가할 하며 트랜잭션이 완료 되기 전에 실행 됩니다. 다른 모든 규칙 이후에 DeletedRules 실행 됩니다. 하나의 규칙 트랜잭션에서 각 변경에 한 번씩 여러 번 실행할 수입니다.  

6. 규칙의 정보를 전달할에서 정보를 저장할 수는 `TransactionContext`합니다. 트랜잭션 동안 유지 관리 되는 사전을 뿐입니다. 이 트랜잭션이 종료 될 때 삭제 됩니다. 각 규칙에서 이벤트 인수에 대 한 액세스를 제공합니다. 규칙은 예측 가능한 순서로 실행 되지 않도록 해야 합니다.  

7. 다른 대안을 고려한 후 규칙을 사용 합니다. 예를 들어 값이 변경 될 때 속성을 업데이트 하려는 경우에 계산된 된 속성을 사용 하는 것이 좋습니다. 크기 또는 모양의 위치를 제한 하려는 경우 사용을 `BoundsRule`입니다. 속성 값 변경에 응답 하려는 경우 추가 `OnValueChanged` 처리기 속성입니다. 자세한 내용은 [에 응답 하 고 변경 내용을 전파](../modeling/responding-to-and-propagating-changes.md)합니다.  

## <a name="example"></a>예제  
 다음 예제에서는 두 요소를 연결 하는 도메인 관계를 인스턴스화할 때 속성을 업데이트 합니다. 사용자가 링크를 다이어그램에서 뿐만 아니라 프로그램 코드 링크를 만드는 경우 때에이 아니라 규칙이 트리거됩니다.  

 이 예제를 테스트 하려면 작업 흐름 솔루션 템플릿을 사용 하 여 DSL을 만들 수 하 고 Dsl 프로젝트의 파일에 다음 코드를 삽입 합니다. 빌드 및 솔루션을 실행 하 고 디버깅 프로젝트에서 샘플 파일을 엽니다. 주석 도형 사이 유동 요소 주석 링크를 그립니다. 주석에서 텍스트를 연결 하는 가장 최근의 요소에 대 한 보고서를 변경 합니다.  

 실제로 일반적으로 용으로 작성 된 DeleteRule 모든 AddRule 합니다.  

```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Microsoft.VisualStudio.Modeling;  

namespace Company.TaskRuleExample  
{  

  [RuleOn(typeof(CommentReferencesSubjects))]  
  public class RoleRule : AddRule  
  {  

    public override void ElementAdded(ElementAddedEventArgs e)  
    {  
      base.ElementAdded(e);  
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;  
      Comment comment = link.Comment;  
      FlowElement subject = link.Subject;  
      Transaction current = link.Store.TransactionManager.CurrentTransaction;  
      // Don't want to run when we're just loading from file:  
      if (current.IsSerializing) return;  
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";  
    }  

  }  

  public partial class TaskRuleExampleDomainModel  
  {  
    protected override Type[] GetCustomDomainModelTypes()  
    {  
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());  
      types.Add(typeof(RoleRule));  
      return types.ToArray();  
    }  
  }  

}  

```  

## <a name="see-also"></a>참고 항목  
 [이벤트 처리기로 모델 외부의 변경 내용 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)   
 [BoundsRules로 모양 위치 및 크기 제한](../modeling/boundsrules-constrain-shape-location-and-size.md)
