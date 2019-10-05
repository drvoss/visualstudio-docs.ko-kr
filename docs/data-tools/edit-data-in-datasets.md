---
title: 데이터 세트의 데이터 편집
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- datasets [Visual Basic], editing data
- data [Visual Studio], editing in datasets
ms.assetid: 50d5c580-fbf7-408f-be70-e63ac4f4d0eb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: eb6651d788979343752fac30c4570d955b53068c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402853"
---
# <a name="edit-data-in-datasets"></a>데이터 세트의 데이터 편집
모든 데이터베이스의 테이블에서 데이터를 편집할 때 처럼 데이터 테이블의에서 데이터를 편집 합니다. 프로세스는 삽입, 업데이트 및 테이블의 레코드를 삭제 하는 중에 포함할 수 있습니다. 데이터 바인딩된 폼에 있는 사용자가 편집 가능한 필드를 지정할 수 있습니다. 이러한 경우 데이터 바인딩 인프라는 모든 변경 내용 추적 나중에 변경 내용을 데이터베이스로 다시 전송 수 있도록 처리 합니다. 프로그래밍 방식으로 데이터를 편집을 수행한 경우 해당 변경 내용을 다시 데이터베이스에 전송 하려는 개체와 수에 대 한 변경 내용 추적을 수행 하는 메서드를 사용 해야 합니다.

실제 데이터를 변경 하는 것 외에도 쿼리할 수도 있습니다는 <xref:System.Data.DataTable> 특정 데이터 행을 반환 합니다. 예를 들어, 개별 행, 행 (원래 및 제안 된)의 특정 버전에서 변경 된 행 또는 오류가 있는 행에 대해 쿼리할 수 있습니다.

## <a name="to-edit-rows-in-a-dataset"></a>데이터 집합의 행을 편집 하려면
기존 행을 편집 하는 <xref:System.Data.DataTable>을 찾아봐야 하는 <xref:System.Data.DataRow> 편집 하 고 원하는 열에 업데이트 된 값을 할당 하려는 합니다.

사용 하 여 편집 하려는 행의 인덱스를 알 수 없는 경우는 `FindBy` 기본 키로 검색 하는 방법.

[!code-csharp[VbRaddataEditing#3](../data-tools/codesnippet/CSharp/edit-data-in-datasets_1.cs)]
[!code-vb[VbRaddataEditing#3](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_1.vb)]

행 인덱스를 알고 있으면 액세스할 수 있고 행을 다음과 같이 편집 합니다.

[!code-csharp[VbRaddataEditing#5](../data-tools/codesnippet/CSharp/edit-data-in-datasets_2.cs)]
[!code-vb[VbRaddataEditing#5](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_2.vb)]

## <a name="to-insert-new-rows-into-a-dataset"></a>데이터 집합에 새 행을 삽입
데이터 바인딩된 컨트롤을 일반적으로 사용 하는 응용 프로그램을 통해 새 레코드를 추가 합니다 **새로 추가** 단추를 [BindingNavigator 컨트롤](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms)합니다.

데이터 집합에 새 레코드를 수동으로 추가 하려면 DataTable에서 메서드를 호출 하 여 새 데이터 행을 만듭니다. 그런 다음 행을 추가 합니다 <xref:System.Data.DataRow> 컬렉션 (<xref:System.Data.DataTable.Rows%2A>)의 <xref:System.Data.DataTable>:

[!code-csharp[VbRaddataEditing#1](../data-tools/codesnippet/CSharp/edit-data-in-datasets_3.cs)]
[!code-vb[VbRaddataEditing#1](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_3.vb)]

데이터 집합을 데이터 원본에 업데이트를 보내는 해야 한다는 정보를 유지 하기 위해 사용 된 <xref:System.Data.DataRow.Delete%2A> 데이터 테이블의 행을 제거 하는 방법입니다. 예를 들어, 응용 프로그램에서 TableAdapter를 사용 하는 경우 (또는 <xref:System.Data.Common.DataAdapter>), TableAdapter의 `Update` 데이터베이스에 있는 행을 삭제 하는 메서드를 <xref:System.Data.DataRow.RowState%2A> 의 <xref:System.Data.DataRowState.Deleted>합니다.

응용 프로그램 업데이트를 다시 데이터 원본에 보낼 필요가 없습니다, 경우 직접 데이터 행 컬렉션에 액세스 하 여 레코드를 제거 하려면 (<xref:System.Data.DataRowCollection.Remove%2A>).

#### <a name="to-delete-records-from-a-data-table"></a>데이터 테이블에서 레코드를 삭제 하려면

- 호출 된 <xref:System.Data.DataRow.Delete%2A> 메서드는 <xref:System.Data.DataRow>합니다.

     이 메서드 레코드를 물리적으로 제거 하지 않습니다. 대신, 삭제에 대 한 레코드를 표시합니다.

    > [!NOTE]
    > count 속성을 표시 하는 경우는 <xref:System.Data.DataRowCollection>, 결과 횟수가 삭제 표시 된 레코드를 포함 합니다. 컬렉션을 반복할 수 있습니다 삭제 용으로 표시 되지 않은 레코드의 정확한 개수를 가져오려면는 <xref:System.Data.DataRow.RowState%2A> 각 레코드의 속성입니다. (삭제 표시 된 레코드를 <xref:System.Data.DataRow.RowState%2A> 의 <xref:System.Data.DataRowState.Deleted>.) 또는 행 상태에 따라 필터링 하는 데이터 집합의 데이터 뷰를 만들 수 있으며 여기에서 count 속성을 가져올 수 있습니다.

다음 예제에서는 호출 하는 방법을 보여 줍니다 합니다 <xref:System.Data.DataRow.Delete%2A> 첫 번째 행을 표시 하는 방법의 `Customers` 테이블 삭제:

[!code-csharp[VbRaddataEditing#8](../data-tools/codesnippet/CSharp/edit-data-in-datasets_4.cs)]
[!code-vb[VbRaddataEditing#8](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_4.vb)]

## <a name="determine-if-there-are-changed-rows"></a>변경 된 행이 있는지 확인
데이터 집합의 레코드를 변경 하는 경우 커밋할 때까지 해당 변경 내용에 대 한 정보 저장 됩니다. 호출할 때 변경 내용을 커밋하는 `AcceptChanges` 메서드를 호출할 때 또는 데이터 집합 또는 데이터 테이블의는 `Update` TableAdapter 또는 데이터 어댑터의 메서드.

변경이 추적 된 두 가지 방법으로 각 데이터 행 합니다.

- 와 관련 된 정보를 포함 하는 각 데이터 행의 <xref:System.Data.DataRow.RowState%2A> (예를 들어 <xref:System.Data.DataRowState.Added>, <xref:System.Data.DataRowState.Modified>, <xref:System.Data.DataRowState.Deleted>, 또는 <xref:System.Data.DataRowState.Unchanged>).

- 해당 행의 여러 버전을 포함 하는 각 변경 된 데이터 행 (<xref:System.Data.DataRowVersion>), (하기 전에 변경) 원래 버전과 (변경) 후 현재 버전입니다. 변경 보류 중인 경우 기간 (에 응답 하는 경우에 <xref:System.Data.DataTable.RowChanging> 이벤트), 세 번째 버전-제안 된 버전-도 사용할 수 있습니다.

합니다 <xref:System.Data.DataSet.HasChanges%2A> 데이터 집합의 반환 `true` 데이터 집합의 변경 된 경우. 에 변경 된 행이 있는지 확인 한 후 호출할 수 있습니다는 `GetChanges` 메서드를 <xref:System.Data.DataSet> 또는 <xref:System.Data.DataTable> 변경 된 행 집합을 반환 합니다.

#### <a name="to-determine-if-changes-have-been-made-to-any-rows"></a>모든 행에 변경 사항이 생겼는지 확인 하려면

- 호출 된 <xref:System.Data.DataSet.HasChanges%2A> 메서드를 확인 하는 데이터 집합의 행을 변경 합니다.

다음 예제에서는 반환 값을 확인 하는 방법의 <xref:System.Data.DataSet.HasChanges%2A> 변경 된 행 이라는 데이터 집합에 있는지 여부를 검색 하는 방법 `NorthwindDataset1`:

[!code-csharp[VbRaddataEditing#12](../data-tools/codesnippet/CSharp/edit-data-in-datasets_5.cs)]
[!code-vb[VbRaddataEditing#12](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_5.vb)]

## <a name="determine-the-type-of-changes"></a>변경 유형을 결정 합니다.
변경의 유형을 확인 하려면에서 만든 데이터 집합에서 값을 전달 하 여 확인할 수도 있습니다는 <xref:System.Data.DataRowState> 열거형을 <xref:System.Data.DataSet.HasChanges%2A> 메서드.

#### <a name="to-determine-what-type-of-changes-have-been-made-to-a-row"></a>확인 하려면 어떤 유형의 변경에 적용 된 행

- 전달 된 <xref:System.Data.DataRowState> 값을 <xref:System.Data.DataSet.HasChanges%2A> 메서드.

다음 예제에서는 명명 된 데이터 집합을 확인 하는 방법을 보여 줍니다 `NorthwindDataset1` 새 행을 추가한 경우를 확인 하려면:

[!code-csharp[VbRaddataEditing#13](../data-tools/codesnippet/CSharp/edit-data-in-datasets_6.cs)]
[!code-vb[VbRaddataEditing#13](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_6.vb)]

## <a name="to-locate-rows-that-have-errors"></a>오류가 있는 행을 찾기 위한
개별 열 및 행의 데이터를 사용할 때 오류가 발생할 수 있습니다. 확인할 수 있습니다 합니다 `HasErrors` 속성에 오류가 있는지 확인 하는 <xref:System.Data.DataSet>를 <xref:System.Data.DataTable>, 또는 <xref:System.Data.DataRow>합니다.

1. 확인 된 `HasErrors` 속성을 데이터 집합에 오류가 있는지 확인 합니다.

2. 경우는 `HasErrors` 속성은 `true`, 테이블의 컬렉션을 반복 차례로 통해 행을 오류 행을 찾습니다.

[!code-csharp[VbRaddataEditing#23](../data-tools/codesnippet/CSharp/edit-data-in-datasets_7.cs)]
[!code-vb[VbRaddataEditing#23](../data-tools/codesnippet/VisualBasic/edit-data-in-datasets_7.vb)]

## <a name="see-also"></a>참고자료

- [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)