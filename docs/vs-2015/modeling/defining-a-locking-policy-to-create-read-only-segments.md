---
title: 잠금 정책을 정의 하 여 읽기 전용 세그먼트 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: fa549c71-2bf6-4b08-b7b2-7756dd6f1dc8
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6044e9c47a0dcbc95fd1503906cbd81ac8e44526
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422650"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>잠금 정책을 정의하여 읽기 전용 세그먼트 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

불변성 API는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Visualization and Modeling SDK을 통해 프로그램에서는 잠금 일부 또는 전체 도메인 특정 언어 (DSL) 모델을 읽을 수 있지만 변경 되지 않도록 합니다. 이 읽기 전용 옵션이 사용할 수 있습니다, 예를 들어 사용자 동료 들이 주석 달기 및 DSL 모델 검토를 요청할 수 있지만 원래 변경에서 차단할 수 있습니다.  
  
 또한 DSL 작성자 정의할 수 있습니다는 *잠금 정책을 합니다.* 잠금 정책을 허용, 허용 되지 않음 또는 필수 되는 잠금을 정의 합니다. 예를 들어 DSL에 게시할 때 새 명령을 사용 하 여 확장 하는 타사 개발자가 게 요청할 수 있습니다. 하지만 모델의 지정 된 파트의 읽기 전용 상태를 변경 하지 못하도록 잠금 정책을 사용할 수도 있습니다.  
  
> [!NOTE]
> 잠금 정책의 리플렉션을 사용 하 여 손상 될 수 있습니다. 이 타사 개발자를 위한 명확한 경계를 제공 하지만 강력한 보안을 제공 하지 않습니다.  
  
 자세한 내용 및 샘플에서 사용할 수는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkId=186128) 웹 사이트입니다.  
  
## <a name="setting-and-getting-locks"></a>설정 및 잠금 가져오기  
 저장소, 파티션을 또는 개별 요소에 대해 잠금을 설정할 수 있습니다. 예를 들어,이 문을 모델 요소를 삭제할 수 없게 됩니다 및 변경 되지 않도록 해당 속성을 방해할 됩니다.  
  
```  
using Microsoft.VisualStudio.Modeling.Immutability; ...  
element.SetLocks(Locks.Delete | Locks.Property);  
```  
  
 다른 잠금 값 관계, 요소 만들기, 파티션 및 역할에 다시 정렬 링크 간에 이동의 변경을 방지 하기 위해 사용할 수 있습니다.  
  
 잠금에는 프로그램 코드 및 사용자 작업에 모두 적용 됩니다. 프로그램 코드 변경을 수행 하려고 하는 경우는 `InvalidOperationException` throw 됩니다. 잠금이 취소 또는 다시 실행 작업에서 무시 됩니다.  
  
 여부를 요소에 모든 잠금을 지정 된 집합을 사용 하 여 검색할 수 있습니다 `IsLocked(Locks)` 를 사용 하 여 요소에 대 한 잠금 현재 집합을 가져올 수 있습니다 및 `GetLocks()`합니다.  
  
 트랜잭션을 사용 하지 않고 잠금을 설정할 수 있습니다. 잠금 데이터베이스 저장소의 일부가 아닙니다. 저장소에서 값의 변경에 대 한 응답에서 잠금을 설정한 경우 예를 들어 OnValueChanged에서 허용 해야 변경 내용을 실행 취소 작업의 일부인.  
  
 이러한 메서드는 정의 된 확장 메서드는 <xref:Microsoft.VisualStudio.Modeling.Immutability> 네임 스페이스입니다.  
  
### <a name="locks-on-partitions-and-stores"></a>파티션 및 저장소에 대 한 잠금  
 잠금이는 파티션 및 저장소에도 적용할 수 있습니다. 잠금을 파티션에 설정 된 파티션에 있는 모든 요소에 적용 됩니다. 따라서 예를 들어, 다음 문을 하면 파티션의 모든 요소 자체 잠금 상태에 관계 없이 삭제할 수 없습니다. 그럼에도 불구 하 고 기타 잠금 수와 같은 `Locks.Property` 여전히 개별 요소에 설정할 수 없습니다.  
  
```  
partition.SetLocks(Locks.Delete);  
```  
  
 저장소에 설정 된 잠금을 파티션과 요소에 해당 잠금 설정에 관계 없이 모든 해당 요소에 적용 됩니다.  
  
### <a name="using-locks"></a>잠금을 사용 하 여  
 다음 예와 같이 체계를 구현 하는 잠금을 사용할 수 있습니다.  
  
- 모든 요소를 제외 하 고 메모를 나타내는 관계는 변경을 허용 하지 않습니다. 이 모델을 변경 하지 않고 주석을 달 수가 있습니다.  
  
- 다이어그램 파티션에 허용 하지만 기본 파티션의 변경 내용을 허용 하지 않습니다. 사용자는 다이어그램을 다시 정렬할 수 있지만 기본 모델을 변경할 수 없습니다.  
  
- 별도 데이터베이스에 등록 된 사용자의 그룹을 제외 하 고 저장소에 변경 내용을 허용 하지 않습니다. 다른 사용자에 대 한 다이어그램 및 모델은 읽기 전용입니다.  
  
- 다이어그램의 부울 속성을 설정 하는 경우 모델 변경 내용 허용 안 함 true로 합니다. 해당 속성을 변경 하는 메뉴 명령을 제공 합니다. 이렇게 하면 해당 하지 않는 사용자가 실수로 변경 합니다.  
  
- 속성 변경은 허용 하지만 추가 및 삭제 요소의 특정 클래스의 관계를 허용 하지 않습니다. 이 속성을 채울 수는 고정된 형식으로 사용자를 제공 합니다.  
  
## <a name="lock-values"></a>잠금 값  
 잠금은 저장소, 파티션 또는 개별 ModelElement에서 설정할 수 있습니다. 잠금이 0이 `Flags` 열거형: 사용 하 여 해당 값을 결합할 수 '&#124;'.  
  
- 이 클래스는 ModelElement의 잠금에는 항상 해당 파티션의 잠금이 포함합니다.  
  
- 파티션의 잠금에는 항상 저장소의 잠금이 포함합니다.  
  
  파티션에서 잠금을 설정 하 고 또는 저장 하 고, 동시에 개별 요소에 대 한 잠금을 사용 하지 않도록 설정 수 없습니다.  
  
|값|즉 경우 `IsLocked(Value)` true|  
|-----------|------------------------------------------|  
|없음|제한이 없습니다.|  
|속성|요소의 도메인 속성을 변경할 수 없습니다. 이 관계의 도메인 클래스의 역할에서 생성 되는 속성에 적용 되지 않습니다.|  
|Add|파티션의 새 요소 및 링크를 만들 수 없습니다 하거나 저장 합니다.<br /><br /> 적용할 수 없는 `ModelElement`합니다.|  
|이동|요소의 경우 파티션 간에 이동할 수 없습니다 `element.IsLocked(Move)` 가 true 이면 이거나 `targetPartition.IsLocked(Move)` 그렇습니다.|  
|삭제|이 잠금이 요소 자체에 설정 하거나는 요소 중 하나에서 삭제 전파, 포함 된 요소와 모양 같은 요소를 삭제할 수 없습니다.<br /><br /> 사용할 수 있습니다 `element.CanDelete()` 요소를 삭제할 수 있는지 여부를 검색 합니다.|  
|다시 정렬|한 roleplayer에 있는 링크의 순서를 변경할 수 없습니다.|  
|RolePlayer|이 요소에 제공 되는 링크의 집합을 변경할 수 없습니다. 예를 들어,이 요소 아래에 있는 새 요소를 포함할 수 없습니다. 이 요소는 대상 링크는 영향을 주지 않습니다.<br /><br /> 이 요소는 링크를 해당 원본과 대상 적용 되지 않습니다.|  
|모두|다른 값의 비트 Or입니다.|  
  
## <a name="locking-policies"></a>잠금 정책  
 DSL의 작성자를 정의할 수 있습니다는 *잠금 정책을*합니다. 잠금 정책을 구체적인 잠금을 설정 또는 특정 잠금을 설정 해야 한다고 위임에서 수 없도록 SetLocks(), 작업을 조정 합니다. 일반적으로 하는 정책을 사용 하 여 잠금 사용자 또는 개발자가 실수로 동일한 방식으로 변수를 선언할 수는 DSL의 용도 contravening에서 억제 `private`합니다.  
  
 요소의 형식에 종속 된 모든 요소에 잠금을 설정 하려면 잠금 정책을 사용할 수도 있습니다. 왜냐하면 `SetLocks(Locks.None)` 는 요소를 처음 만들거나 파일에서 deserialize 할 때 항상 호출 됩니다.  
  
 그러나 요소에 대 한 잠금이 해당 수명 동안 변경 하는 정책의 사용할 수 없습니다. 에 대 한 호출을 사용 해야 해당 효과 달성 하려면 `SetLocks()`합니다.  
  
 잠금 정책을 정의 하려면를 지정 해야 합니다.  
  
- <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>를 구현하는 클래스를 만듭니다.  
  
- DSL의 DocData를 통해 사용할 수 있는 서비스에이 클래스를 추가 합니다.  
  
### <a name="to-define-a-locking-policy"></a>잠금 정책을 정의 하려면  
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 다음 정의 있습니다.  
  
```  
public interface ILockingPolicy  
{  
  Locks RefineLocks(ModelElement element, Locks proposedLocks);  
  Locks RefineLocks(Partition partition, Locks proposedLocks);  
  Locks RefineLocks(Store store, Locks proposedLocks);  
}  
```  
  
 이러한 메서드를 호출할 때 호출 됩니다 `SetLocks()` 저장소, 파티션 또는 모델 요소에 있습니다. 각 메서드에서 잠금의 제안된 집합으로 제공 됩니다. 제안 된 집합을 반환할 수 있습니다 또는 추가 하 고 잠금 뺄 수 있습니다.  
  
 예를 들어:  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{  
  public class MyLockingPolicy : ILockingPolicy  
  {  
    /// <summary>  
    /// Moderate SetLocks(this ModelElement target, Locks locks)  
    /// </summary>  
    /// <param name="element">target</param>  
    /// <param name="proposedLocks">locks</param>  
    /// <returns></returns>  
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)  
    {  
      // In my policy, users can never delete an element,  
      // and other developers cannot easily change that:  
      return proposedLocks | Locks.Delete);  
    }  
    public Locks RefineLocks(Store store, Locks proposedLocks)  
    {  
      // Only one user can change this model:  
      return Environment.UserName == "aUser"   
           ? proposedLocks : Locks.All;  
    }  
  
```  
  
 다른 코드를 호출 하는 경우에 사용자는 요소를 삭제할 수 있는지 확인 하려면 `SetLocks(Lock.Delete):`  
  
 `return proposedLocks & (Locks.All ^ Locks.Delete);`  
  
 모든 요소의 MyClass의 모든 속성 변경 허용 되지 않습니다.  
  
 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`  
  
### <a name="to-make-your-policy-available-as-a-service"></a>정책을 서비스로 사용할 수 있도록 하려면  
 사용자 `DslPackage` 프로젝트에서 다음 예제와 비슷한 코드를 포함 하는 새 파일을 추가 합니다.  
  
```  
using Microsoft.VisualStudio.Modeling;  
using Microsoft.VisualStudio.Modeling.Immutability;  
namespace Company.YourDsl.DslPackage // Change  
{   
  // Override the DocData GetService() for this DSL.  
  internal partial class YourDslDocData // Change  
  {  
    /// <summary>  
    /// Custom locking policy cache.  
    /// </summary>  
    private ILockingPolicy myLockingPolicy = null;  
  
    /// <summary>  
    /// Called when a service is requested.  
    /// </summary>  
    /// <param name="serviceType">Service requested</param>  
    /// <returns>Service implementation</returns>  
    public override object GetService(System.Type serviceType)  
    {  
      if (serviceType == typeof(SLockingPolicy)   
       || serviceType == typeof(ILockingPolicy))  
      {  
        if (myLockingPolicy == null)  
        {  
          myLockingPolicy = new MyLockingPolicy();  
        }  
        return myLockingPolicy;  
      }  
      // Request is for some other service.  
      return base.GetService(serviceType);  
    }  
}  
```
