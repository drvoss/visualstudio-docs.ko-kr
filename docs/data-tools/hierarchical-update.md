---
title: 계층적 업데이트
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, changed data
- data [Visual Basic], hierarchical update
- saving updated data
- datasets [Visual Basic], hierarchical update
- hierarchical update
- saving data, hierarchical update
- modified data saving
- updated data saving
- related tables, saving
ms.assetid: 68bae3f6-ec9b-45ee-a33a-69395029f54c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a15daaf5ac98bc2efc4ce83bb2370b94e9f59123
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745467"
---
# <a name="hierarchical-update"></a>계층적 업데이트

*계층적 업데이트* 무결성 규칙을 유지 하면서 데이터베이스에 다시 (둘 이상의 관련된 테이블을 사용 하 여 데이터 집합)에서 업데이트 된 데이터를 저장 하는 프로세스를 가리킵니다. *참조 무결성* 삽입, 업데이트 및 삭제 관련된 레코드의 동작을 제어 하는 데이터베이스에서 제약 조건에 의해 제공 되는 일관성 규칙을 가리킵니다. 예를 들어 참조 무결성 적용 해당 고객에 대 한 주문을 만들 수 있도록 허용 하기 전에 고객 레코드를 생성 하는 것입니다.  데이터 집합의 관계에 대 한 자세한 내용은 참조 하세요. [데이터 집합의 관계](../data-tools/relationships-in-datasets.md)합니다.

계층적 업데이트 기능을 사용 하는 `TableAdapterManager` 관리 하는 `TableAdapter`형식화 된 데이터 집합의 합니다. `TableAdapterManager` 구성 요소는 Visual Studio에서 생성 된 클래스를.NET 형식이 아닙니다. 테이블을 끌면 합니다 **데이터 원본** 폼 이나 페이지에서 TableAdapterManager 형식의 변수를 추가 하는 Windows Form 또는 WPF 페이지에서 Visual Studio 창 및 구성 요소 트레이에 디자이너에 표시 합니다. 에 대 한 자세한 내용은 합니다 `TableAdapterManager` 클래스의 TableAdapterManager 참조 섹션을 참조 하십시오 [Tableadapter](../data-tools/create-and-configure-tableadapters.md)합니다.

기본적으로 데이터 집합 취급 관련된 테이블 "관계에만 해당" 즉, foreign key 제약 조건을 강제 적용 하지 않습니다. 사용 하 여 디자인 타임에 해당 설정을 수정할 수 있습니다 합니다 **데이터 집합 디자이너**합니다. 표시 하기 위해 두 테이블 간의 관계 선을 선택 합니다 **관계** 대화 상자. 여기에서 수행한 변경 내용을 결정 하는 방법을 `TableAdapterManager` 때 동작 변경 내용이 관련된 테이블의 데이터베이스에 다시 보내는 것입니다.

## <a name="enable-hierarchical-update-in-a-dataset"></a>데이터 집합에서 계층적 업데이트를 사용 하도록 설정

기본적으로 계층적 업데이트는 프로젝트에서 생성 되거나 추가 되는 모든 새 데이터 집합에 대 한 설정 됩니다. 설정 하 여 계층적 업데이트를 켜거나 끌 합니다 **계층적 업데이트** 데이터 집합의 형식화 된 데이터 집합 속성 **True** 하거나 **False**:

![계층적 업데이트 설정](../data-tools/media/hierarchical-update-setting.png)

## <a name="create-a-new-relation-between-tables"></a>테이블 간에 새 관계를 만들려면

두 테이블 간에 새 관계를 만들려면 데이터 집합 디자이너에서 각 테이블의 제목 표시줄을 선택, 한 다음 마우스 오른쪽 단추로 **관계 추가**합니다.

![계층적 업데이트 관계가 메뉴 추가](../data-tools/media/hierarchical-update-add-relation-menu.png)

## <a name="understand-foreign-key-constraints-cascading-updates-and-deletes"></a>Foreign key 제약 조건, 연계 업데이트 및 삭제를 이해 합니다.

어떻게 foreign key 제약 조건을 이해 해야 하 고 생성 된 데이터 집합 코드에서 만들어진 데이터베이스의 동작을 연계 합니다.

기본적으로 데이터 집합에 있는 데이터 테이블 관계를 사용 하 여 생성 됩니다 (<xref:System.Data.DataRelation>)과 일치 하는 데이터베이스의 관계. 그러나 데이터 집합에서 관계는 외래 키 제약 조건으로 생성 되지 않습니다. 합니다 <xref:System.Data.DataRelation> 로 구성 됩니다 **관계만** 없이 <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> 또는 <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> 적용 합니다.

기본적으로 연속 업데이트 및 삭제는 해제 되어 연속 업데이트를 사용 하 여 데이터베이스 관계를 설정 및/또는 설정 삭제를 연계 하는 경우에 합니다. 예를 들어, 새 고객을 만들고 새 주문을 다음 데이터를 저장 하는 동안 발생할 수 있습니다 충돌 하는 데이터베이스에 정의 된 외래 키 제약 조건. 자세한 내용은 [데이터 집합을 채우는 동안 제약 조건 해제](turn-off-constraints-while-filling-a-dataset.md)합니다.

## <a name="set-the-order-to-perform-updates"></a>업데이트를 수행 하는 순서를 설정 합니다.

집합의 개별 주문 삽입, 업데이트 및 삭제 하는 업데이트를 수행 하는 순서를 설정 합니다. 데이터 집합의 모든 테이블의 수정된 된 모든 데이터를 저장 하려면 필요 합니다. 계층적 업데이트를 사용 하는 경우 삽입 먼저 수행 하는 다음 업데이트 및 삭제 합니다. 합니다 `TableAdapterManager` 제공을 `UpdateOrder` 먼저 업데이트를 수행 하는 집합을 삽입 및 삭제 될 수 있는 속성입니다.

> [!NOTE]
> 업데이트 순서는 모두 포괄 이해 하는 것이 반드시 합니다. 즉, 업데이트가 수행 된 삽입 및 삭제 데이터 집합의 모든 테이블에 대해 수행 됩니다.

설정 하는 `UpdateOrder` 에서 항목을 위로 끌어 놓은 후 속성을를 [데이터 소스 창](add-new-data-sources.md#data-sources-window) 폼으로 선택는 `TableAdapterManager` 구성 요소 트레이를 설정을 `UpdateOrder` 속성에는 **속성** 창입니다.

## <a name="create-a-backup-copy-of-a-dataset-before-performing-a-hierarchical-update"></a>계층적 업데이트를 수행 하기 전에 백업 복사본을 데이터 집합 만들기

데이터를 저장 하는 경우 (호출 하 여 합니다 `TableAdapterManager.UpdateAll()` 메서드), `TableAdapterManager` 단일 트랜잭션에서 각 테이블에 대 한 데이터를 업데이트 하려고 합니다. 모든 테이블에 대 한 업데이트의 일부가 실패 하면 전체 트랜잭션이 롤백됩니다. 대부분의 경우 롤백이를 원래 상태로 응용 프로그램을 반환합니다.

그러나 경우에 따라 백업 복사본에서 데이터 집합을 복원 해야 할 수 있습니다. 이 한 가지 예는 자동 증분 값을 사용 하는 경우에 발생할 수 있습니다. 예를 들어, 저장 작업은 실패, 데이터 집합에서는 자동 증분 값 재설정 되지 않습니다 및 자동 증분 값을 만들려는 데이터 집합을 계속 합니다. 이런 응용 프로그램에서 사용할 수 없는 번호에 간격이 있습니다. 상황에 여기서 문제는이 `TableAdapterManager` 제공을 `BackupDataSetBeforeUpdate` 트랜잭션이 실패할 경우 백업 복사본을 사용 하 여 기존 데이터 집합을 대체 하는 속성입니다.

> [!NOTE]
> 백업 복사본은 하는 동안 메모리에만 `TableAdapterManager.UpdateAll` 메서드를 실행 합니다. 따라서 있습니다 이므로이 백업 데이터 집합에 프로그래밍 방식으로 액세스할 수 없습니다 원래 데이터 집합을 대체 하거나 범위를 벗어날 즉시는 `TableAdapterManager.UpdateAll` 메서드 실행이 완료 합니다.

## <a name="modify-the-generated-save-code-to-perform-the-hierarchical-update"></a>생성 된 저장 계층적 업데이트를 수행 하는 코드 수정

`TableAdapterManager.UpdateAll` 메서드를 호출한 다음 관련 테이블이 포함된 데이터 세트의 이름을 전달하여 데이터 세트의 관련 데이터 테이블에서 데이터베이스로 변경 내용을 저장합니다. 예를 들어 NorthwindDataset에 포함된 모든 테이블의 업데이트를 백 엔드 데이터베이스로 보내려면 `TableAdapterManager.UpdateAll(NorthwindDataset)` 메서드를 실행합니다.

**데이터 원본** 창에서 항목을 놓으면 코드가 `Form_Load` 이벤트에 자동으로 추가되어 각 테이블을 채웁니다(`TableAdapter.Fill` 메서드). 또한 데이터 세트의 데이터를 데이터베이스에 다시 저장할 수 있도록 <xref:System.Windows.Forms.BindingNavigator>의 **저장** 단추 클릭 이벤트에도 코드가 추가됩니다(`TableAdapterManager.UpdateAll` 메서드).

생성된 저장 코드에는 `CustomersBindingSource.EndEdit` 메서드를 호출하는 코드 줄도 포함됩니다. 호출 보다 구체적으로 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 메서드의 첫 번째 <xref:System.Windows.Forms.BindingSource>폼에 추가 된 합니다. 즉,이 코드는만에서 끌어 첫 번째 테이블에 대 한 생성 된 **데이터 원본** 창에서 폼입니다. <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 호출에서는 현재 편집 중인 데이터 바인딩된 컨트롤의 프로세스에 포함된 모든 변경 내용을 커밋합니다. 따라서 데이터 바인딩된 컨트롤에 계속 포커스가 있는 상태에서 **저장** 단추를 클릭하면 실제 저장 전에 해당 컨트롤에서 보류 중인 모든 편집 내용이 커밋됩니다(`TableAdapterManager.UpdateAll` 메서드).

> [!NOTE]
> **데이터 집합 디자이너** 만 추가 된 `BindingSource.EndEdit` 폼에 놓은 첫 번째 테이블에 대 한 코드입니다. 그러므로 폼의 각 관련 테이블에 대해 `BindingSource.EndEdit` 메서드를 호출하는 코드 줄을 추가해야 합니다. 이 연습에서는 `OrdersBindingSource.EndEdit` 메서드 호출을 추가해야 합니다.

### <a name="to-update-the-code-to-commit-changes-to-the-related-tables-before-saving"></a>저장 전에 관련 테이블로 변경 내용을 커밋하도록 코드를 업데이트하려면

1. <xref:System.Windows.Forms.BindingNavigator>에서 **저장** 단추를 두 번 클릭하여 코드 편집기에서 **Form1**을 엽니다.

2. `OrdersBindingSource.EndEdit` 메서드를 호출하는 줄 뒤에 `CustomersBindingSource.EndEdit` 메서드를 호출하는 코드 줄을 추가합니다. **저장** 단추 클릭 이벤트 내의 코드는 다음과 같습니다.

     [!code-vb[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/VisualBasic/hierarchical-update_1.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#1](../data-tools/codesnippet/CSharp/hierarchical-update_1.cs)]

이처럼 데이터를 데이터베이스에 저장하기 전에 관련 자식 테이블에 대해 변경 내용을 커밋해야 할 뿐 아니라 새 자식 레코드를 데이터 세트에 추가하기 전에 새로 만든 부모 레코드도 커밋해야 할 수 있습니다. 즉, 새 부모 레코드를 추가 할 수 있습니다 (`Customer`) foreign key 제약 조건을 새 자식 레코드를 사용 하도록 설정 하기 전에 데이터 집합에 (`Orders`) 데이터 집합을 추가할 수 있습니다. 자식 `BindingSource.AddingNew` 이벤트를 사용하면 이 작업을 수행할 수 있습니다.

> [!NOTE]
> 새 부모 레코드를 적용 해야 하는지 여부를 데이터 원본에 바인딩하는 데 사용 되는 컨트롤의 유형에 따라 달라 집니다. 이 연습에서는 개별 컨트롤을 사용 하 여 부모 테이블에 바인딩합니다. 이 새 부모 레코드를 커밋하는 추가 코드가 필요 합니다. 같은 부모 레코드 대신 복잡 한 바인딩 컨트롤에서 표시 된 경우는 <xref:System.Windows.Forms.DataGridView>이 추가 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> 부모 레코드가 필요 하지 않을 것에 대 한 호출 합니다. 컨트롤의 기본 데이터 바인딩 기능이 새 레코드 커밋을 처리하기 때문입니다.

### <a name="to-add-code-to-commit-parent-records-in-the-dataset-before-adding-new-child-records"></a>새 자식 레코드를 추가하기 전에 데이터 세트에서 부모 레코드를 커밋하는 코드를 추가하려면

1. `OrdersBindingSource.AddingNew` 이벤트에 대한 이벤트 처리기를 만듭니다.

    - 오픈 **Form1** 디자인 뷰에서 선택 **OrdersBindingSource** 구성 요소 트레이에 선택 **이벤트** 에 **속성** 창 및 다음 두 번 클릭 합니다 **AddingNew** 이벤트입니다.

2. 호출 하는 이벤트 처리기에 코드 줄을 추가 합니다 `CustomersBindingSource.EndEdit` 메서드. `OrdersBindingSource_AddingNew` 이벤트 처리기의 코드는 다음과 같습니다.

     [!code-vb[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/VisualBasic/hierarchical-update_2.vb)]
     [!code-csharp[VSProDataOrcasHierarchicalUpdate#2](../data-tools/codesnippet/CSharp/hierarchical-update_2.cs)]

## <a name="tableadaptermanager-reference"></a>TableAdapterManager 참조

기본적으로 `TableAdapterManager` 클래스 관련된 테이블이 포함 된 데이터 집합을 만들 때 생성 됩니다. 클래스 생성을 방지 하려면 값을 변경 합니다 `Hierarchical Update` false 데이터 집합의 속성입니다. Windows Form 또는 WPF 페이지의 디자인 화면으로 관계가 있는 테이블을 끌어 놓으면 Visual Studio 클래스의 멤버 변수를 선언 합니다. 데이터 바인딩을 사용 하지 않는 경우 수동으로 변수를 선언 해야 합니다.

`TableAdapterManager` 클래스는.NET 형식이 아닙니다. 따라서 설명서에서를 찾을 수 없습니다. 데이터 집합 만들기 프로세스의 일부로 디자인 타임에 생성 됩니다.

다음은 자주 사용 되는 메서드 및 속성을 `TableAdapterManager` 클래스:

|멤버|설명|
|------------|-----------------|
|`UpdateAll` 메서드|모든 데이터 테이블에서 모든 데이터를 저장합니다.|
|`BackUpDataSetBeforeUpdate` 속성|실행 하기 전에 데이터 집합의 백업 복사본을 만들지 여부를 결정 합니다 `TableAdapterManager.UpdateAll` 메서드. 부울 값입니다.|
|*tableName* `TableAdapter` 속성|나타냅니다는 `TableAdapter`합니다. 생성 된 `TableAdapterManager` 각각에 대 한 속성을 포함 `TableAdapter` 관리 합니다. 예를 들어, Customers 및 Orders 테이블이 포함 된 데이터 집합 사용 하 여 생성 됩니다는 `TableAdapterManager` 포함 된 `CustomersTableAdapter` 및 `OrdersTableAdapter` 속성입니다.|
|`UpdateOrder` 속성|개별 insert, update 및 delete 명령 순서를 제어합니다. 이 설정의 값 중 하나에 `TableAdapterManager.UpdateOrderOption` 열거형입니다.<br /><br /> 기본적으로 `UpdateOrder` 로 설정 된 **InsertUpdateDelete**합니다. 이 즉, 삽입, 업데이트 하 고 삭제 한 다음 데이터 집합의 모든 테이블에 대해 수행 됩니다.|

## <a name="see-also"></a>참고자료

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
