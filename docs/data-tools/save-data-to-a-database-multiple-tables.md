---
title: 데이터베이스에 데이터 저장(여러 테이블)
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9e4a30c3aa85969a4cbf712f2f4018c24169ff6d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565905"
---
# <a name="save-data-to-a-database-multiple-tables"></a>데이터베이스에 데이터 저장(여러 테이블)

애플리케이션 개발에서 가장 일반적인 시나리오는 Windows 애플리케이션의 폼에 데이터를 표시하고 데이터를 편집한 다음 업데이트된 데이터를 데이터베이스로 다시 보내는 것입니다. 이 연습에서는 두 관련 테이블의 데이터를 표시하는 폼을 만들고, 레코드를 편집한 다음 변경 내용을 데이터베이스에 다시 저장하는 방법을 보여줍니다. 이 예에서는 Northwind 샘플 데이터베이스의 `Customers` 및 `Orders` 테이블을 사용합니다.

TableAdapter의 `Update` 메서드를 호출하여 애플리케이션의 데이터를 데이터베이스에 다시 저장할 수 있습니다. 테이블을 끌면 합니다 **데이터 원본** 창에서 폼에 데이터를 저장 하는 데 필요한 코드를 자동으로 추가 됩니다. 이 코드를 수동으로 추가 해야 하는 추가 테이블이 있는 폼에 추가 됩니다. 이 연습에서는 둘 이상의 테이블에서 업데이트를 저장하는 코드를 추가하는 방법을 보여줍니다.

이 연습에서 설명하는 작업은 다음과 같습니다.

- 만들기 및 사용 하 여 응용 프로그램에서 데이터 원본을 구성 합니다 [데이터 소스 구성 마법사](../data-tools/media/data-source-configuration-wizard.png)합니다.

- 에 있는 항목의 컨트롤을 설정 합니다 [데이터 소스 창](add-new-data-sources.md#data-sources-window)합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)합니다.

- **데이터 원본** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만듭니다.

- 데이터 집합의 각 테이블에서 몇 가지 레코드를 수정 합니다.

- 데이터 세트의 업데이트된 데이터를 데이터베이스로 다시 보내도록 코드를 수정합니다.

## <a name="prerequisites"></a>전제 조건

이 연습에서는 Northwind 샘플 데이터베이스 및 SQL Server Express LocalDB를 사용 합니다.

1. SQL Server Express LocalDB가 없는 경우 설치에서 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express), 또는 합니다 **Visual Studio 설치 관리자**합니다. 에 **Visual Studio 설치 관리자**의 일부로 SQL Server Express LocalDB를 설치할 수 있습니다는 **데이터 저장 및 처리** 워크 로드 또는 개별 구성 요소로 합니다.

2. 다음이 단계를 수행 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

    1. Visual Studio에서 엽니다는 **SQL Server 개체 탐색기** 창입니다. (SQL Server 개체 탐색기의 일부로 설치 되는 **데이터 저장소 및 처리** Visual Studio 설치 관리자에서 작업 합니다.) 확장 된 **SQL Server** 노드. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 선택 **새 쿼리**합니다.

       쿼리 편집기 창이 열립니다.

    2. 복사 합니다 [Northwind Transact SQL 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 클립보드에 있습니다. 이 T-SQL 스크립트부터에서 Northwind 데이터베이스를 만들고 데이터로 채웁니다.

    3. T-SQL 스크립트, 쿼리 편집기에 붙여넣고 선택한 합니다 **Execute** 단추입니다.

       짧은 시간 후 쿼리 실행이 완료 하 고 Northwind 데이터베이스 생성 됩니다.

## <a name="create-the-windows-forms-application"></a>Windows Forms 응용 프로그램 만들기

새 **Windows Forms 앱** 프로젝트에 대 한 C# 또는 Visual Basic입니다. 프로젝트 이름을 **UpdateMultipleTablesWalkthrough**로 지정합니다.

## <a name="create-the-data-source"></a>데이터 원본 만들기

이 단계에서는 **데이터 원본 구성 마법사**를 사용하여 Northwind 데이터베이스에서 데이터 원본을 만듭니다. 연결을 만들려면 Northwind 샘플 데이터베이스에 액세스해야 합니다. Northwind 샘플 데이터베이스 설정에 대 한 자세한 내용은 [방법: 예제 데이터베이스 설치](../data-tools/installing-database-systems-tools-and-samples.md)합니다.

1. 에 **데이터** 메뉴에서 **데이터 소스 표시**합니다.

   **데이터 원본** 창이 열립니다.

2. **데이터 원본** 창에서 **새 데이터 원본 추가**를 선택하여 **데이터 원본 구성 마법사**를 시작합니다.

3. 에 **데이터 소스 형식 선택** 화면에서 **데이터베이스**를 선택한 후 **다음**합니다.

4. 에 **데이터 연결 선택** 화면에서 다음 중 하나를 수행 합니다.

    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

         또는

    - **새 연결**을 선택하여 **연결 추가 또는 수정** 대화 상자를 엽니다.

5. 데이터베이스에서 암호를 요구 하는 경우 중요 한 데이터를 포함 하 여 선택한 옵션을 선택 **다음**합니다.

6. 에 **응용 프로그램 구성 파일에 연결 문자열을 저장**를 선택 **다음**합니다.

7. 에 **데이터베이스 개체 선택** 화면에서 확장 된 **테이블** 노드.

8. 선택 합니다 **고객** 하 고 **주문** 테이블을 선택한 후 **마침**.

     **NorthwindDataSet**가 프로젝트에 추가되고 테이블이 **데이터 원본** 창에 나타납니다.

## <a name="set-the-controls-to-be-created"></a>만들 컨트롤 설정

이 연습에서는 데이터에는 `Customers` 테이블은는 **세부 정보** 레이아웃 데이터를 개별 컨트롤에에서 표시 되는 위치입니다. 데이터를 `Orders` 테이블은는 **표** 레이아웃에 표시 되는 <xref:System.Windows.Forms.DataGridView> 컨트롤.

### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>데이터 소스 창에서 항목에 대한 삭제 유형을 설정하려면

1. 에 **데이터 원본** 창 확장 합니다 **고객** 노드.

2. 에 **고객** 노드를 선택 **세부 정보** 의 컨트롤을 변경 하 고 컨트롤 목록에서를 **고객** 테이블을 개별 컨트롤로 합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)합니다.

## <a name="create-the-data-bound-form"></a>데이터 바인딩된 폼을 만들려면

**데이터 원본** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만들 수 있습니다.

1. 주 **Customers** 노드를 **데이터 원본** 창에서 **Form1**으로 끌어서 놓습니다.

     설명 레이블이 있는 데이터 바인딩된 컨트롤이 레코드 탐색을 위한 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>와 함께 폼에 나타납니다. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)를 `CustomersTableAdapter`를 <xref:System.Windows.Forms.BindingSource>, 및 <xref:System.Windows.Forms.BindingNavigator> 구성 요소 트레이에 나타납니다.

2. 관련 **Orders** 노드를 **데이터 원본** 창에서 **Form1**으로 끌어 옵니다.

    > [!NOTE]
    > **Fax** 열 아래에 있는 관련 **Orders** 노드는 **Customers** 노드의 자식 노드입니다.

     <xref:System.Windows.Forms.DataGridView> 컨트롤과 레코드 탐색에 사용되는 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>가 폼에 나타납니다. `OrdersTableAdapter` 고 <xref:System.Windows.Forms.BindingSource> 구성 요소 트레이에 나타납니다.

## <a name="add-code-to-update-the-database"></a>데이터베이스를 업데이트 하는 코드를 추가 합니다.

**Customers** 및 **Orders** TableAdapters의 `Update` 메서드를 호출하여 데이터베이스를 업데이트할 수 있습니다. 기본적으로 대 한 이벤트 처리기를 **저장** 단추를<xref:System.Windows.Forms.BindingNavigator> 데이터베이스로 업데이트를 보내는 폼의 코드에 추가 됩니다. 이 절차에서는 올바른 순서로 업데이트를 보내는 코드를 수정 합니다. 이 참조 무결성 오류 발생 가능성을 제거 합니다. 또한 이 코드는 try-catch 블록에서 업데이트 호출을 래핑하여 오류 처리를 구현합니다. 애플리케이션의 요구 사항에 맞게 코드를 수정할 수 있습니다.

> [!NOTE]
> 이해를 돕기 위해이 연습에는 트랜잭션을 사용 하지 않습니다. 그러나 두 업데이트 하는 경우 테이블 관련 트랜잭션 내에서 모든 업데이트 논리를 포함 합니다. 트랜잭션은 모든 변경 내용이 커밋되기 전에 모든 관련된 변경 내용이 데이터베이스에는 성공적으로 만드는 프로세스입니다. 자세한 내용은 [트랜잭션 및 동시성](/dotnet/framework/data/adonet/transactions-and-concurrency)합니다.

### <a name="to-add-update-logic-to-the-application"></a>애플리케이션에 업데이트 논리를 추가하려면

1. 선택 된 **저장** 단추를 <xref:System.Windows.Forms.BindingNavigator>입니다. 코드 편집기에 열립니다는 `bindingNavigatorSaveItem_Click` 이벤트 처리기입니다.

2. 관련 TableAdapter의 `Update` 메서드를 호출하도록 이벤트 처리기의 코드를 바꿉니다. 다음 코드는 먼저 각 <xref:System.Data.DataRowState>(<xref:System.Data.DataRowState.Deleted>, <xref:System.Data.DataRowState.Added> 및 <xref:System.Data.DataRowState.Modified>)에 대해 업데이트된 정보를 저장할 3개 임시 데이터 테이블을 만듭니다. 업데이트를 올바른 순서로 실행 됩니다. 이 코드는 다음과 같습니다.

     [!code-vb[VbRaddataSaving#10](../data-tools/codesnippet/VisualBasic/save-data-to-a-database-multiple-tables_1.vb)]
     [!code-csharp[VbRaddataSaving#10](../data-tools/codesnippet/CSharp/save-data-to-a-database-multiple-tables_1.cs)]

## <a name="test-the-application"></a>애플리케이션 테스트

1. **F5**키를 누릅니다.

2. 각 테이블에 포함된 레코드 하나 이상의 데이터를 변경해 봅니다.

3. **저장** 단추를 선택합니다.

4. 데이터베이스의 값을 점검하여 변경 내용이 저장되었는지 확인합니다.

## <a name="see-also"></a>참고자료

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)