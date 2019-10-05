---
title: '방법: 트랜잭션을 사용하여 모델 업데이트'
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a7514e3ff0c876a669f514a7e17bb02b73c19c2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936851"
---
# <a name="how-to-use-transactions-to-update-the-model"></a>방법: 트랜잭션을 사용하여 모델 업데이트
트랜잭션에 저장소에 대 한 변경 내용을 그룹으로 처리할지 있는지 확인 합니다. 그룹화 된 변경 내용은 커밋 또는 단일 단위로 롤백될 수 있습니다.

 프로그램 코드 수정, 추가, Visual Studio Visualization and Modeling SDK 저장소의 임의 요소가 삭제 될 때마다 해당 트랜잭션 내에서 수행 해야 합니다. 활성 인스턴스가 있어야 <xref:Microsoft.VisualStudio.Modeling.Transaction> 변경이 발생할 때 저장소와 연결 합니다. 이 모든 모델 요소, 관계, 모양, 다이어그램 및 해당 속성에 적용 됩니다.

 트랜잭션 메커니즘을 통해 일관 되지 않은 상태를 방지할 수 있습니다. 트랜잭션 중에 오류가 발생 하는 경우 모든 변경 내용이 롤백됩니다. 사용자는 실행 취소 명령의 수행 하는 경우에 단일 단계로 각 최근 트랜잭션 처리 됩니다. 사용자는 개별 트랜잭션에 명시적으로 저장 하지 않는 한 최근의 변경, 부분을 취소할 수 없습니다.

## <a name="opening-a-transaction"></a>트랜잭션을 열기
 트랜잭션을 관리 하는 가장 편리한 방법은 된를 `using` 묶인 문을 `try...catch` 문:

```csharp
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 경우 마지막을 방지 하는 예외가 `Commit()` 저장소를 이전 상태로 다시 설정 됩니다 변경 하는 동안 발생 합니다. 이렇게 하면는 오류를 벗어나지 모델 일관성이 없는 상태에 있는지 확인 합니다.

 단일 트랜잭션 내에서 원하는 만큼을 만들 수 있습니다. 새 트랜잭션이 활성 트랜잭션 내에서 열 수 있습니다. 중첩 된 트랜잭션이 커밋 또는 포함 하는 트랜잭션 종료 되기 전에 롤백할 해야 합니다. 자세한 내용은 참조에 대 한 예제는 <xref:Microsoft.VisualStudio.Modeling.Transaction.TransactionDepth%2A> 속성.

 해야 변경 내용을 영구적으로 유지 되도록, `Commit` 트랜잭션을 삭제 하기 전에 합니다. 예외가 발생 하는 트랜잭션에서 잡히지 않는 저장소 상태로 변경 하기 전에 다시 설정 됩니다.

## <a name="rolling-back-a-transaction"></a>트랜잭션 롤백
 저장소를 유지 하거나 트랜잭션이 이전 상태로 되돌아갑니다 않도록, 다음이 전략 중 하나를 사용할 수 있습니다.

1. 트랜잭션의 범위 내에서 잡히지 않는 예외가 발생 합니다.

2. 명시적 트랜잭션을 롤백하십시오.

    ```csharp
    this.Store.TransactionManager.CurrentTransaction.Rollback();
    ```

## <a name="transactions-do-not-affect-non-store-objects"></a>트랜잭션이 아닌 저장소 개체에 영향을 주지 않습니다.
 트랜잭션만 저장소의 상태를 제어합니다. 이러한 파일, 데이터베이스 또는 DSL 정의 외부에서 일반 형식으로 선언 해야 하는 개체와 같은 외부 항목에 적용 된 부분 변경 내용을 취소할 수 없습니다.

 예외가 남았을 이러한 변경의 저장소를 사용 하 여 일관 되지 않은, 예외 처리기의 가능성을 처리 해야 합니다. 외부 리소스 저장소 개체를 사용 하 여 동기화 된 상태로 유지 되도록 한 방법은 이벤트 처리기를 사용 하 여 저장소의 요소에는 각 외부 개체를 결합 하는 것입니다. 자세한 내용은 [이벤트 처리기 전파 변경 외부 모델](../modeling/event-handlers-propagate-changes-outside-the-model.md)합니다.

## <a name="rules-fire-at-the-end-of-a-transaction"></a>트랜잭션이 끝날 때 규칙 실행
 트랜잭션의 끝 트랜잭션이 삭제 되기 전에 스토어에서 요소에 연결 하는 규칙 발생 합니다. 각 규칙은 변경 된 모델 요소에 적용 되는 메서드입니다. 예를 들어, "수정" 규칙이 해당 모델 요소에 변경 되 면 셰이프 상태를 업데이트 하는 만들고 있는 셰이프를 모델 요소를 만들 때. 지정 된 발생 순서가 없습니다. 규칙에서 변경한 내용이 다른 규칙을 발생할 수 있습니다.

 사용자 고유의 규칙을 정의할 수 있습니다. 규칙에 대 한 자세한 내용은 참조 하세요. [에 응답 하 고 변경 내용을 전파](../modeling/responding-to-and-propagating-changes.md)합니다.

 규칙을 실행 취소, 다시 실행, 또는 롤백 명령 후 발생 하지 않습니다.

## <a name="transaction-context"></a>트랜잭션 컨텍스트
 각 트랜잭션에 사전 원하는 정보를 저장할 수 있습니다.

 `store.TransactionManager`

 `.CurrentTransaction.TopLevelTransaction`

 `.Context.Add(aKey, aValue);`

 규칙 간에 정보를 전송할 경우 특히 유용 합니다.

## <a name="transaction-state"></a>트랜잭션 상태
 방지 하기 위해 필요한 경우도 변경 실행 취소 중 또는 트랜잭션을 다시 실행 하 여 발생 하는 경우 변경 내용을 전파 합니다. 이 발생할 수 있습니다, 예를 들어 저장소의 다른 값을 업데이트할 수 있는 속성 값 처리기를 작성 하는 경우. 실행 취소 작업 저장소에 있는 모든 값을 이전 상태로 다시 설정 되므로 업데이트 된 값을 계산 하는 데 필요하지 없습니다. 이 코드를 사용 합니다.

```csharp
if (!this.Store.InUndoRedoOrRollback) {...}
```

 규칙은 저장소 파일에서 처음 로드 되는 경우에 발생할 수 있습니다. 이러한 변경에 응답을 방지 하려면 다음을 사용 합니다.

```csharp
if (!this.Store.InSerializationTransaction) {...}
```