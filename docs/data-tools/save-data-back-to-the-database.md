---
title: 데이터를 다시 데이터베이스에 저장
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], validating data
- data validation, datasets
- data [Visual Studio], saving
- row version
- updating datasets, constraints
- datasets [Visual Basic], about datasets
- datasets [Visual Basic], merging
- updates, constraints in datasets
- saving data, about saving data
- datasets [Visual Basic], constraints
- TableAdapters
ms.assetid: afe6cb8a-dc6a-428b-b07b-903ac02c890b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 31b41a9c18a9e055c9d144c7115d3673ee2e4443
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566592"
---
# <a name="save-data-back-to-the-database"></a>데이터를 다시 데이터베이스에 저장

데이터 집합에는 데이터의 메모리 내 복사본입니다. 해당 데이터를 수정할 경우 해당 변경 내용을 다시 데이터베이스에 저장 하는 것이 좋습니다. 이렇게 하면 세 가지 방법 중 하나에서:

- 하나를 호출 하 여 `Update` TableAdapter의 메서드

- 중 하나를 호출 하 여 `DBDirect` TableAdapter의 메서드

- 호출 하 여는 `UpdateAll` TableAdapterManager 데이터 집합에 데이터 집합의 다른 테이블에 관련 테이블을 포함 하는 경우 Visual Studio를 생성 하는 메서드

데이터에 바인딩하는 경우 데이터 집합 테이블을 Windows Form 또는 XAML 페이지 컨트롤에 데이터 바인딩 아키텍처를 모든 작업을 수행 합니다.

Tableadapter에 익숙한 경우에 다음이 항목 중 하나에 직접 이동할 수 있습니다.

|항목|설명|
|-----------|-----------------|
|[데이터베이스에 새 레코드 삽입](../data-tools/insert-new-records-into-a-database.md)|수행 하는 방법을 업데이트 하 고 Tableadapter 또는 명령 개체를 사용 하 여 삽입|
|[TableAdapter를 사용하여 데이터 업데이트](../data-tools/update-data-by-using-a-tableadapter.md)|Tableadapter 사용 하 여 업데이트를 수행 하는 방법|
|[계층적 업데이트](../data-tools/hierarchical-update.md)|둘 이상의 관련된 테이블을 사용 하 여 데이터 집합에서 업데이트를 수행 하는 방법|
|[동시성 예외 처리](../data-tools/handle-a-concurrency-exception.md)|두 사용자가 동시에 데이터베이스에서 동일한 데이터를 변경 하려고 할 때 예외를 처리 하는 방법|
|[방법: 트랜잭션을 사용하여 데이터 저장](../data-tools/save-data-by-using-a-transaction.md)|시스템을 사용 하 여 트랜잭션에서 데이터를 저장 하는 방법입니다. Transactions 네임 스페이스와 TransactionScope 개체|
|[트랜잭션에 데이터 저장](../data-tools/save-data-in-a-transaction.md)|트랜잭션 내에서 데이터베이스에 데이터를 저장 하는 중 보여 주기 위해 Windows Forms 응용 프로그램을 만드는 연습|
|[데이터베이스에 데이터 저장(여러 테이블)](../data-tools/save-data-to-a-database-multiple-tables.md)|레코드를 편집 하 고 다시 데이터베이스에 여러 테이블에 변경 내용을 저장 하는 방법|
|[개체에서 데이터베이스로 데이터 저장](../data-tools/save-data-from-an-object-to-a-database.md)|TableAdapter DbDirect 메서드를 사용 하 여 데이터베이스에 데이터 집합에 없는 개체에서 데이터를 전달 하는 방법|
|[TableAdapter DBDirect 메서드를 사용하여 데이터 저장](../data-tools/save-data-with-the-tableadapter-dbdirect-methods.md)|TableAdapter를 사용 하 여 SQL 쿼리를 데이터베이스로 직접 보내는 방법|
|[데이터 세트를 XML로 저장](../data-tools/save-a-dataset-as-xml.md)|XML 문서에 데이터 집합을 저장 하는 방법|

## <a name="two-stage-updates"></a>2 단계 업데이트

데이터 소스를 업데이트 하는 것은 2 단계 프로세스입니다. 첫 번째 단계는 삭제 된 레코드 또는 변경 된 레코드를 사용 하는, 새 레코드를 사용 하 여 데이터 집합을 업데이트 하는 것입니다. 응용 프로그램 변경 내용을 데이터 소스에 다시 전송 하지, 다음 경우 업데이트를 사용 하 여 완료 합니다.

변경 내용을 데이터베이스로 다시 보내는 경우 두 번째 단계는 필요 합니다. 데이터 바인딩된 컨트롤을 사용 하지 않는 경우 수동으로 호출 하 여 `Update` 같은 TableAdapter (또는 데이터 어댑터)의 데이터 집합을 채우는 데 사용 하는 메서드. 그러나 하나의 데이터 원본에서 데이터 이동 하거나 여러 데이터 원본을 업데이트 하려면 예를 들어, 다양 한 어댑터를 사용할 수도 있습니다. 데이터 바인딩을 사용 하지 않는 하 고 관련된 테이블의 변경 내용을 저장 하는 경우 자동으로 생성 된 변수를 수동으로 인스턴스화할 필요가 `TableAdapterManager` 클래스 및 호출 후 해당 `UpdateAll` 메서드.

![데이터 집합 업데이트의 개념적 다이어그램](../data-tools/media/vbdatasetupdates.gif)

데이터 집합 행의 컬렉션을 포함 하는 테이블의 컬렉션을 포함 합니다. 내부 데이터 소스를 나중에 업데이트 하려는 경우에 메서드를 사용 해야는 `DataTable.DataRowCollection` 행 추가 또는 제거 하는 경우에 속성입니다. 이러한 메서드는 데이터 원본을 업데이트 하는 것에 대 한 필요한 변경 내용 추적을 수행 합니다. 호출 하는 경우는 `RemoveAt` 컬렉션 행 속성에 삭제가 데이터베이스에 다시 전달 되지 않습니다.

## <a name="merge-datasets"></a>데이터 집합 병합

데이터 집합의 콘텐츠를 업데이트할 수 있습니다 *병합* 다른 데이터 집합을 사용 하 여 합니다. 내용을 복사 하는 것이 *소스* 호출 데이터 집합에 데이터 집합 (라고 합니다 *대상* 데이터 집합). 데이터 집합을 병합 하면 원본 데이터 집합에서 새 레코드를 대상 데이터 집합에 추가 됩니다. 또한 원본 데이터 집합에서 여분의 열은 대상 데이터 집합에 추가 됩니다. 데이터 집합 병합 로컬 데이터 집합이 있고 다른 응용 프로그램에서 두 번째 데이터 집합을 표시 하는 경우 유용 합니다. XML 웹 서비스와 같은 구성 요소에서 두 번째 데이터 집합을 가져올 때 또는 여러 데이터 집합의 데이터를 통합 하는 경우에 유용 합니다.

데이터 집합을 병합 하는 경우 부울 인수를 전달할 수 있습니다 (`preserveChanges`)을 설명 하는 <xref:System.Data.DataSet.Merge%2A> 메서드 기존 수정 대상 데이터 집합에 유지할지 여부를 합니다. 레코드의 여러 버전을 유지 하는 데이터 집합 이므로 레코드의 버전이 둘 이상 병합 되는 점을 염두 해야 합니다. 다음 표에서 두 개의 데이터 집합에서 레코드를 병합 하는 방법을 보여 줍니다.

|DataRowVersion|대상 데이터 세트|원본 데이터 집합|
| - | - | - |
|원래 색|James Wilson|James C. Wilson|
|현재|Jim Wilson|James C. Wilson|

호출 된 <xref:System.Data.DataSet.Merge%2A> 메서드를 사용 하 여 이전 테이블 `preserveChanges=false targetDataset.Merge(sourceDataset)` 다음 데이터에서 결과:

|DataRowVersion|대상 데이터 세트|원본 데이터 집합|
| - | - | - |
|원래 색|James C. Wilson|James C. Wilson|
|현재|James C. Wilson|James C. Wilson|

호출 된 <xref:System.Data.DataSet.Merge%2A> 메서드를 사용 하 여 `preserveChanges = true targetDataset.Merge(sourceDataset, true)` 다음 데이터에서 결과:

|DataRowVersion|대상 데이터 세트|원본 데이터 집합|
| - | - | - |
|원래 색|James C. Wilson|James C. Wilson|
|현재|Jim Wilson|James C. Wilson|

> [!CAUTION]
> 에 `preserveChanges = true` 시나리오에서는 경우는 <xref:System.Data.DataSet.RejectChanges%2A> 메서드는 대상 데이터 집합의 레코드에 대해 다음 원본 데이터로 돌아갑니다를 *원본* 데이터 집합. 즉, 대상 데이터 집합을 사용 하 여 원래 데이터 소스를 업데이트 하려고 하면 원래 행 업데이트를 찾을 수 없습니다. 데이터 원본에서 업데이트 된 레코드를 사용 하 여 다른 데이터 집합을 채운 다음 동시성 위반을 방지 하기 위해 병합을 수행 하는 동시성 위반을 방지할 수 있습니다. (동시성 위반을 데이터 집합을 채워진 후 다른 사용자가 데이터 소스의 레코드를 수정할 때 발생 합니다.)

## <a name="update-constraints"></a>제약 조건 업데이트

기존 데이터 행을 변경 하려면 추가 하거나 개별 열에 데이터를 업데이트 합니다. 데이터 집합 제약 조건 (예: 외래 키 또는 null이 아닌 제약 조건)에 있으면 가능으로 업데이트 하 고 레코드 오류 상태의 수 일시적으로 있습니다. 즉, 하나의 열 업데이트를 완료 하지만 다음에 도달 하기 전에 오류 상태에서 수 있습니다.

중간 제약 조건 위반을 방지 하기 위해 업데이트 제약 조건을 일시적으로 중단할 수 있습니다. 이 두 가지 용도로 사용 됩니다.

- 오류가 발생 한 열을 업데이트를 완료 하지만 다른 업데이트를 시작 하지 않은 throw 되지 않도록 합니다.

- 특정 업데이트 하는 것을 방지 되는 이벤트 발생 (유효성 검사를 위해 자주 사용 되는 이벤트).

> [!NOTE]
> Datagrid에 기본 제공 되는 데이터 바인딩 아키텍처는 Windows Forms에서 제약 조건 검사 포커스를 행 외부로 이동 하 고 명시적으로 호출할 필요가 없습니다 될 때까지 일시 중단 합니다 <xref:System.Data.DataRow.BeginEdit%2A>, <xref:System.Data.DataRow.EndEdit%2A>, 또는 <xref:System.Data.DataRow.CancelEdit%2A> 메서드.

제약 조건은 자동으로 비활성화 될 때를 <xref:System.Data.DataSet.Merge%2A> 메서드는 데이터 집합에서 호출 됩니다. 병합이 완료 되 면 사용할 수 없는 데이터 집합의 모든 제약 조건이 있는 경우는 <xref:System.Data.ConstraintException> throw 됩니다. 이 이런 경우에 <xref:System.Data.DataSet.EnforceConstraints%2A> 속성이로 설정 되어 `false,` 다시 설정 하기 전에 모든 제약 조건 위반을 해결 해야 합니다 <xref:System.Data.DataSet.EnforceConstraints%2A> 속성을 `true`입니다.

업데이트를 완료 한 후 다시 활성화할 수 있습니다 제약 조건 검사 이벤트를 발생 시킨 및는 다시 업데이트 이벤트를 사용 하도록 설정 합니다.

이벤트를 일시 중단 하는 방법에 대 한 자세한 내용은 참조 하세요. [데이터 집합을 채우는 동안 제약 조건 해제](../data-tools/turn-off-constraints-while-filling-a-dataset.md)합니다.

## <a name="dataset-update-errors"></a>데이터 집합 업데이트 오류

데이터 집합의 레코드를 업데이트할 때 오류 가능성입니다. 예를 들어 열에 잘못 된 형식의 데이터 또는 너무 깁니다. 또는 데이터 무결성 문제가 있는 실수로 작성할 수 있습니다. 또는 업데이트 이벤트의 모든 단계에서 사용자 지정 오류를 발생 시킬 수 있는 응용 프로그램별 유효성 검사를 해야 할 수 있습니다. 자세한 내용은 [데이터 집합의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)합니다.

## <a name="maintain-information-about-changes"></a>변경 내용에 대 한 정보를 유지 관리

데이터 집합의 변경 내용에 대 한 정보는 두 가지 방법으로 유지 관리: 행 변경 내용이 있는지 여부를 나타내는 플래그를 지정 하 여 (<xref:System.Data.DataRow.RowState%2A>), 레코드의 여러 복사본을 유지 하 고 (<xref:System.Data.DataRowVersion>). 이 정보를 사용 하 여 프로세스는 데이터 집합에서 변경 된 내용을 결정 하 고 데이터 원본에 적절 한 업데이트를 보낼 수 있습니다.

### <a name="rowstate-property"></a>RowState 속성

합니다 <xref:System.Data.DataRow.RowState%2A> 의 속성을 <xref:System.Data.DataRow> 개체는 데이터의 특정 행의 상태에 대 한 정보를 제공 하는 값입니다.

다음 표에서 설명의 가능한 값은 <xref:System.Data.DataRowState> 열거형:

|DataRowState 값|설명|
| - |-----------------|
|<xref:System.Data.DataRowState.Added>|에 항목으로 행이 추가 <xref:System.Data.DataRowCollection>합니다. (이 상태에서 행을 해당 하는 원래 버전에 존재 하지 않기 때문 때 마지막 <xref:System.Data.DataRow.AcceptChanges%2A> 메서드를 호출한).|
|<xref:System.Data.DataRowState.Deleted>|사용 하 여 행이 삭제 합니다 <xref:System.Data.DataRow.Delete%2A> 의 <xref:System.Data.DataRow> 개체입니다.|
|<xref:System.Data.DataRowState.Detached>|행 생성 되었지만의 일부가 아닌 <xref:System.Data.DataRowCollection>합니다. <xref:System.Data.DataRow> 즉시이 만들어진 후 전에 추가한 컬렉션 및 컬렉션에서 제거 된 후이 상태 개체입니다.|
|<xref:System.Data.DataRowState.Modified>|행의 열 값은 어떤 방식으로든에서 변경 되었습니다.|
|<xref:System.Data.DataRowState.Unchanged>|행이 이후 변경 되지 <xref:System.Data.DataRow.AcceptChanges%2A> 가 마지막으로 호출 합니다.|

### <a name="datarowversion-enumeration"></a>DataRowVersion 열거형

데이터 집합 레코드의 여러 버전을 유지 합니다. <xref:System.Data.DataRowVersion> 필드에 값을 검색 하는 경우 사용 됩니다는 <xref:System.Data.DataRow> 를 사용 하 여를 <xref:System.Data.DataRow.Item%2A> 속성 또는 <xref:System.Data.DataRow.GetChildRows%2A> 메서드를 <xref:System.Data.DataRow> 개체입니다.

다음 표에서 설명의 가능한 값은 <xref:System.Data.DataRowVersion> 열거형:

|DataRowVersion 값|설명|
| - |-----------------|
|<xref:System.Data.DataRowVersion.Current>|레코드의 현재 버전이 포함 된 마지막 시간 이후 레코드에서 수행 된 모든 수정 <xref:System.Data.DataRow.AcceptChanges%2A> 호출 되었습니다. 행이 삭제 된 경우 현재 버전이 없습니다.|
|<xref:System.Data.DataRowVersion.Default>|데이터 집합 스키마 또는 데이터 원본에 의해 정의 된 레코드의 기본 값입니다.|
|<xref:System.Data.DataRowVersion.Original>|레코드의 원래 버전 레코드의 복사본은 데이터 집합의 변경 내용이 마지막으로 커밋된 것입니다. 실질적으로 이것이 일반적으로 레코드의 버전으로 읽기 데이터 원본에서입니다.|
|<xref:System.Data.DataRowVersion.Proposed>|제안 된 레코드는 업데이트 중에 동안 일시적으로 사용할 수 있는 버전-즉, 시간 사이 라는 합니다 <xref:System.Data.DataRow.BeginEdit%2A> 메서드 및 <xref:System.Data.DataRow.EndEdit%2A> 메서드. 일반적으로 액세스 이벤트 처리기에서 레코드의 제안된 된 버전 같은 <xref:System.Data.DataTable.RowChanging>합니다. 호출 된 <xref:System.Data.DataRow.CancelEdit%2A> 메서드 하면 변경 내용을 취소 하 고 데이터 행의 제안된 된 버전을 삭제 합니다.|

원래 버전과 현재 버전은 업데이트 정보는 데이터 원본에 전송 될 때 유용 합니다. 일반적으로, 데이터 원본에 대 한 업데이트를 보낼 때 데이터베이스에 대 한 새 정보 레코드의 현재 버전입니다. 원본 버전에서 정보는 업데이트할 레코드를 찾고 사용 됩니다.

예를 들어, 레코드의 기본 키가 변경 된 경우에서 변경 내용을 업데이트 하려면 데이터 원본에서 레코드를 올바르게 찾을 수 있는 방법이 필요 합니다. 원래 버전이 없으면, 다음 레코드는 레코드를 원하지 않는 여분의 뿐만 아니라 부정확 하 고 만료 된 하나의 레코드에서 결과 데이터 원본에 추가할 가능성이 있습니다. 두 버전 동시성 제어에도 사용 됩니다. 레코드 데이터 집합에 로드 된 이후 변경 되었는지 여부를 확인 하려면 데이터 원본에서 레코드에 대 한 원래 버전을 비교할 수 있습니다.

제안 된 버전 실제로 데이터 집합에 변경 내용을 커밋하기 전에 유효성 검사를 수행 해야 할 때 유용 합니다.

레코드를 변경 하는 경우에 않습니다 항상 해당 행의 원래 또는 현재 버전입니다. 테이블에 새 행을 삽입 하면 현재 버전만 없는 원래 버전이 있습니다. 마찬가지로, 테이블의 호출 하 여 행을 삭제 하면 `Delete` 메서드를 원래 버전만 있지만 현재 버전이 없습니다.

레코드의 특정 버전 데이터 행을 쿼리하여 존재 하는지 테스트할 수 있습니다 <xref:System.Data.DataRow.HasVersion%2A> 메서드. 레코드의 버전 중 하나를 전달 하 여 액세스할 수 있습니다는 <xref:System.Data.DataRowVersion> 열의 값을 요청 하는 경우 선택적 인수로 열거형 값입니다.

## <a name="get-changed-records"></a>변경 된 레코드 가져오기

데이터 집합의 모든 레코드를 사용 하는 일반적인이 좋습니다. Windows Forms를 사용 하 여 사용자를 사용할 수 있습니다 예를 들어 <xref:System.Windows.Forms.DataGridView> 레코드 수를 표시 하는 컨트롤입니다. 그러나 사용자 수 업데이트 소수의 레코드만, 하나를 삭제 및 삽입 새로 합니다. 메서드를 제공 하는 데이터 집합 및 데이터 테이블 (`GetChanges`) 수정 된 행만 반환 합니다.

사용 하 여 변경 된 레코드의 하위 집합을 만들 수 있습니다 합니다 `GetChanges` 데이터 테이블의 메서드 (<xref:System.Data.DataTable.GetChanges%2A>) 또는 데이터 집합 (<xref:System.Data.DataSet.GetChanges%2A>) 자체입니다. 데이터 테이블에 대 한 메서드를 호출 하는 경우에 변경 된 레코드를 사용 하 여 테이블의 복사본을 반환 합니다. 마찬가지로, 데이터 집합에서 메서드를 호출 하는 경우에 변경 된 레코드를 사용 하 여 새 데이터 집합을 가져옵니다.

`GetChanges` 자체적으로 변경 된 모든 레코드를 반환합니다. 이와 대조적으로 전달한 후 원하는 <xref:System.Data.DataRowState> 매개 변수로 `GetChanges` 메서드를 원하는 변경된 레코드의 하위 집합을 지정할 수 있습니다: 새로 분리 된 레코드를 삭제 표시 된 레코드를 추가 또는 수정 된 레코드입니다.

변경 된 레코드의 하위 집합 가져오기 처리를 위해 다른 구성 요소에 레코드를 보내려고 할 때 유용 합니다. 전체 데이터 집합을 전송 하는 대신 구성 요소에서 필요로 하는 레코드만 가져와서 다른 구성 요소와 통신 하는 오버 헤드를 줄일 수 있습니다.

## <a name="commit-changes-in-the-dataset"></a>데이터 집합의 변경 내용 커밋

데이터 집합에서 변경 되는 <xref:System.Data.DataRow.RowState%2A> 변경 된 행의 속성을 설정 합니다. 레코드의 원래 버전과 현재 버전은 설정, 유지 관리 하 고에서 사용자에 게 제공 된 <xref:System.Data.DataRowView.RowVersion%2A> 속성입니다. 이러한 변경 된 행의 속성에 저장 된 메타 데이터는 데이터 원본에 올바른 업데이트를 전송 하는 데 필요한 합니다.

데이터 소스의 현재 상태를 반영 하는 변경 내용을, 하는 경우이 정보를 유지 관리 해야 하는 더 이상. 일반적으로 두 번 데이터 집합 및 해당 원본에서 동기화는 경우

- 즉시 원본에서 데이터를 읽을 때와 같은 데이터 집합에 정보를 로드 해야 합니다.

- 데이터 원본에 변경 데이터 집합에서 보낸 후 (전이 아니라 데이터베이스에 변경 내용을 전송 하는 데 필요한 변경 내용은 잃게 되므로).

호출 하 여 데이터 집합에 보류 중인 변경 내용을 커밋할 수 있습니다는 <xref:System.Data.DataSet.AcceptChanges%2A> 메서드. 일반적으로 <xref:System.Data.DataSet.AcceptChanges%2A> 시간 이라고 합니다.

- 한 후 데이터 집합을 로드 합니다. TableAdapter를 호출 하 여 데이터 집합을 로드 하는 경우 `Fill` 메서드를 다음 어댑터 자동으로 변경 내용을 커밋하고 있습니다. 그러나 다른 데이터 집합을 병합 하 여 데이터 집합을 로드 하는 경우 다음 해야 수동으로 변경 내용을 커밋해야 합니다.

    > [!NOTE]
    > 호출할 때 변경 내용을 자동으로 커밋할 어댑터를 방지할 수 있습니다 합니다 `Fill` 설정 하 여 메서드를 `AcceptChangesDuringFill` 어댑터의 속성 `false`합니다. 로 설정 된 경우 `false`, 해당 <xref:System.Data.DataRow.RowState%2A> 로 설정 되어 채우기 중에 삽입 되는 각 행의 <xref:System.Data.DataRowState.Added>합니다.

- 한 후 데이터 집합 변경 내용을 XML 웹 서비스와 같은 다른 프로세스에 보냅니다.

    > [!CAUTION]
    > 이 방법은 변경을 커밋한 변경 정보가 지워집니다. 데이터 집합의 어떤 변경 사항이 생겼는지 알아야 응용 프로그램 필요로 하는 작업을 수행 하지 커밋 변경 될 때까지 한 후 완료 수행 합니다.

이 메서드는 다음을 수행합니다.

- 기록 합니다 <xref:System.Data.DataRowVersion.Current> 버전에는 레코드의 해당 <xref:System.Data.DataRowVersion.Original> 버전 원래 버전을 덮어씁니다.

- 모든 행을 제거 위치를 <xref:System.Data.DataRow.RowState%2A> 속성이 <xref:System.Data.DataRowState.Deleted>합니다.

- 설정 된 <xref:System.Data.DataRow.RowState%2A> 는 레코드의 속성 <xref:System.Data.DataRowState.Unchanged>합니다.

<xref:System.Data.DataSet.AcceptChanges%2A> 메서드는 세 가지 수준에서 사용할 수 있습니다. 호출할 수 있습니다는 <xref:System.Data.DataRow> 해당 행에 대 한 커밋 개체를 변경 합니다. 호출할 수도 <xref:System.Data.DataTable> 테이블의 모든 행을 커밋하는 개체입니다. 마지막으로,에서 호출할 수는 <xref:System.Data.DataSet> 데이터 집합의 모든 테이블의 모든 레코드의 모든 보류 중인 변경 내용을 커밋하는 개체입니다.

다음 표에서 변경 내용이 커밋되기에서 메서드는 개체에 따라 보여 줍니다.

|메서드|결과|
|------------|------------|
|<xref:System.Data.DataRow.AcceptChanges%2A?displayProperty=fullName>|특정 행에만 변경 내용이 커밋됩니다.|
|<xref:System.Data.DataTable.AcceptChanges%2A?displayProperty=fullName>|특정 테이블의 모든 행에 변경 내용이 커밋됩니다.|
|<xref:System.Data.DataSet.AcceptChanges%2A?displayProperty=fullName>|데이터 집합의 모든 테이블의 모든 행에 변경 내용이 커밋됩니다.|

> [!NOTE]
> TableAdapter를 호출 하 여 데이터 집합을 로드 하는 경우 `Fill` 메서드를 필요가 없습니다 변경 내용을 명시적으로 적용 합니다. 기본적으로 `Fill` 메서드 호출을 `AcceptChanges` 데이터 테이블 채우기 완료 된 후에 메서드.

관련된 메서드 <xref:System.Data.DataSet.RejectChanges%2A>를 복사 하 여 변경의 효과 실행 합니다 <xref:System.Data.DataRowVersion.Original> 버전에 다시를 <xref:System.Data.DataRowVersion.Current> 레코드의 버전. 또한 설정 합니다 <xref:System.Data.DataRow.RowState%2A> 의 각 레코드 다시 <xref:System.Data.DataRowState.Unchanged>입니다.

## <a name="data-validation"></a>데이터 유효성 검사

응용 프로그램에서 데이터에 전달 되는 프로세스의 요구 사항을 충족 하는지 확인 하기 위해 종종 유효성 검사를 추가 해야 합니다. 이 폼에서 사용자가 입력도 정보 구성 요소 내에서 계산 되는 데이터 원본의 제약 조건에 속하는지 확인 하거나 다른 응용 프로그램에서 응용 프로그램에 전송 되는 데이터를 유효성을 검사할 올바른 인지 확인을 수행할 수도 있습니다. 및 응용 프로그램 요구 사항

여러 가지 방법으로 데이터를 확인할 수 있습니다.

- 비즈니스 계층에서 데이터의 유효성을 검사 하도록 응용 프로그램 코드를 추가 하 여 합니다. 데이터 집합을 한 곳이 수행할 수 있습니다. 데이터 집합을 백 엔드 유효성 검사의 장점 중 일부를 제공 합니다.-열 및 행 값을 변경 하는 변경의 유효성을 검사 하는 기능과 같은 합니다. 자세한 내용은 [데이터 집합의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)합니다.

- 프레젠테이션 레이어의 양식에 유효성 검사를 추가 하 여 합니다. 자세한 내용은 [Windows Forms에서 사용자 입력 유효성 검사](/dotnet/framework/winforms/user-input-validation-in-windows-forms)를 참조하세요.

- 데이터 원본에 데이터를 전송 하 여 백 엔드에서 데이터에서-예를 들어 데이터베이스-수락 하거나 데이터를 거부할 수 있도록 지원 합니다. 복잡 한 데이터 유효성 검사 및 오류 정보를 제공 하는 기능에는 데이터베이스를 사용 하 여 작업 하는 경우에서 제공 되는 위치에 관계 없이 데이터의 유효성을 검사 하기 때문에 실질적인 방법이 될 수 있습니다. 그러나이 방법은 응용 프로그램별 유효성 검사 요구 사항을 허용 하지 않을 수 있습니다. 또한 데이터 소스 데이터의 유효성을 검사 수 발생할 다양 한 왕복에 응용 프로그램 백 엔드에 의해 발생 하는 유효성 검사 오류 확인을 용이 하 게 하는 방법에 따라 데이터 원본에 합니다.

   > [!IMPORTANT]
   > 데이터 명령을 사용 하는 경우는 <xref:System.Data.SqlClient.SqlCommand.CommandType%2A> 로 설정 된 속성 <xref:System.Data.CommandType.Text>, 신중 하 게 데이터베이스에 전달 하기 전에 클라이언트에서 전송 되는 정보를 확인 합니다. 악의적인 사용자가 인증되지 않은 액세스 권한을 얻거나 데이터베이스를 손상시키기 위해 수정되었거나 추가된 SQL 문을 전송(주입)할 수도 있습니다. 데이터베이스에 사용자 입력을 전송 하기 전에 항상 정보가 유효한 지 확인 합니다. 매개 변수가 있는 쿼리 또는 저장된 프로시저를 가능 하면 항상 사용 하는 것이 좋습니다.

## <a name="transmit-updates-to-the-data-source"></a>데이터 원본에 대 한 업데이트를 전송 합니다.

데이터 집합을 변경한 후에 데이터 원본에 변경 내용을 전송할 수 있습니다. 가장 일반적으로이 호출 하 여 수행 된 `Update` TableAdapter (또는 데이터 어댑터) 메서드. 데이터 테이블의 각 레코드 메서드 반복 어떤 유형의 업데이트가 필요한 확인 (업데이트, 삽입 또는 삭제), 한 다음 적절 한 명령을 실행 합니다.

업데이트를 적용 하는 방법을 보여 줍니다, 응용 프로그램에서 단일 데이터 테이블을 포함 하는 데이터 집합을 사용 한다고 가정 합니다. 응용 프로그램 데이터베이스에서 두 개의 행을 인출 합니다. 검색이 수행 된 후 메모리 내 데이터 테이블은 다음과 같습니다.

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Unchanged)    c400         Nancy Buchanan    Pending
```

[기본 설정] Nancy 선하라의 상태를 변경 하는 응용 프로그램 값이이 변경으로 인해 합니다 <xref:System.Data.DataRow.RowState%2A> 에서 해당 행에 대 한 속성 변경 <xref:System.Data.DataRowState.Unchanged> 에 <xref:System.Data.DataRowState.Modified>입니다. 값을 <xref:System.Data.DataRow.RowState%2A> 첫 번째 행에 대 한 속성 유지 <xref:System.Data.DataRowState.Unchanged>합니다. 데이터 테이블은 이제 다음과 같이 표시 됩니다.

```sql
(RowState)     CustomerID   Name             Status
(Unchanged)    c200         Robert Lyon      Good
(Modified)     c400         Nancy Buchanan    Preferred
```

이제 애플리케이션에서 `Update` 메서드를 호출하여 데이터 세트을 데이터베이스로 전송합니다. 메서드는 각 행을 다시 검사합니다. 첫 번째 행에 대해 메서드를 해당 행에는 데이터베이스에서 원래 페치된 이후로 변경 되지 않았기 때문 SQL 문이 없는 데이터베이스에 전송 합니다.

그러나 두 번째 행에 대 한는 `Update` 메서드에서 자동으로 올바른 데이터 명령을 호출 하 고 데이터베이스로 전송 합니다. 특정 SQL 문의 구문을 내부 데이터 저장소에서 지원 되는 SQL의 언어에 따라 달라 집니다. 그러나 전송 된 SQL 문을 다음과 같은 일반 특성은 중요 한:

- 전송된 된 SQL 문과 UPDATE 문의 경우 때문에 UPDATE 문을 사용 하 여에 어댑터를 알고 있는 값을 <xref:System.Data.DataRow.RowState%2A> 속성은 <xref:System.Data.DataRowState.Modified>합니다.

- UPDATE 문의 대상이 행 임을 나타내는 WHERE 절을 포함 하는 전송 된 SQL 문이 여기서 `CustomerID = 'c400'`합니다. 때문에이 부분에서는 SELECT 문은 다른 모든 사용자 로부터 대상 행을 구별 합니다 `CustomerID` 대상 테이블의 기본 키가 있습니다. WHERE 절은 레코드의 원래 버전에서 파생 하는 것에 대 한 정보 (`DataRowVersion.Original`) 행을 식별 하는 데 필요한 값을 변경한 경우.

- 전송 된 SQL 문을 수정 된 열의 새 값을 설정 하는 SET 절을 포함 합니다.

   > [!NOTE]
   > 경우 TableAdapter의 `UpdateCommand` 속성 저장된 프로시저의 이름으로 설정 된 경우 어댑터는 SQL 문을 생성 하지 않습니다. 대신 전달 된 적절 한 매개 변수를 사용 하 여 저장된 프로시저를 호출 합니다.

## <a name="pass-parameters"></a>매개 변수 전달

일반적으로 매개 변수를 사용 하 여 데이터베이스에서 업데이트 하려는 레코드에 대 한 값을 전달 합니다. 경우 TableAdapter의 `Update` 는 UPDATE 문을 실행 하는 메서드, 매개 변수 값을 입력 해야 합니다. 이러한 값을 가져와서를 `Parameters` 적절 한 데이터 명령에 대 한 컬렉션-이 경우는 `UpdateCommand` TableAdapter의 개체입니다.

데이터 어댑터를 생성 하는 Visual Studio 도구를 사용한 경우를 `UpdateCommand` 문 각 매개 변수 자리 표시자에 해당 하는 매개 변수의 컬렉션을 포함 하는 개체입니다.

<xref:System.Data.SqlClient.SqlParameter.SourceColumn%2A?displayProperty=fullName> 각 매개 변수의 속성 데이터 테이블의 열을 가리킵니다. 예를 들어를 `SourceColumn` 속성에 대 한는 `au_id` 및 `Original_au_id` 매개 변수 작성자 id를 포함 하는 데이터 테이블의 모든 열으로 설정 됩니다. 때 어댑터의 `Update` 메서드 실행, 업데이트 되 고를 문에 값을 채우는 레코드의 작성자를 id 열 읽습니다.

UPDATE 문에서 새 값을 모두 지정 (하는 레코드를 쓸) 뿐만 아니라 이전 값 (있도록 레코드를 데이터베이스에 있을 수 있습니다) 해야 합니다. 따라서 두 개의 매개 변수는 각 값에 대 한 합니다: SET 절 및 WHERE 절에 서로 대 한 합니다. 두 매개 변수 데이터 업데이트 되는 레코드에서 읽지만 된 매개 변수에 따라 열 값의 서로 다른 버전을 받게 <xref:System.Data.SqlClient.SqlParameter.SourceVersion> 속성입니다. SET 절에 대 한 매개 변수는 현재 버전을 가져오고 WHERE 절에 대 한 매개 변수는 원래 버전을 가져옵니다.

> [!NOTE]
> 값을 설정할 수도 있습니다는 `Parameters` 컬렉션 데이터 어댑터의 이벤트 처리기에서 일반적으로 수행 하는 코드에서 직접 <xref:System.Data.DataTable.RowChanging> 이벤트입니다.

## <a name="see-also"></a>참고자료

- [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)
- [TableAdapter 만들기 및 구성](create-and-configure-tableadapters.md)
- [TableAdapter를 사용하여 데이터 업데이트](../data-tools/update-data-by-using-a-tableadapter.md)
- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [데이터 유효성 검사](validate-data-in-datasets.md)
- [방법: 추가, 수정 및 삭제 (WCF data services)](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)