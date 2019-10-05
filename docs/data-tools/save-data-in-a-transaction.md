---
title: '연습: 트랜잭션에 데이터 저장'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ea312ca2858a02bc8a70c3e41dbb525c9d222adc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565719"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>연습: 트랜잭션에 데이터 저장

이 연습에서는 사용 하 여 트랜잭션에서 데이터를 저장 하는 방법에 설명 합니다 <xref:System.Transactions> 네임 스페이스입니다. 이 연습에서는 Windows Forms 응용 프로그램을 만들어야 합니다. 데이터 소스 구성 마법사를 사용 하 여 Northwind 샘플 데이터베이스에서 두 테이블에 대 한 데이터 집합을 만드는 것입니다. 데이터 바인딩된 컨트롤을 Windows form 및 BindingNavigator의 save 단추는 TransactionScope 내에서 데이터베이스를 업데이트 하려면 코드를 수정 하겠습니다를 추가 합니다.

## <a name="prerequisites"></a>전제 조건

이 연습에서는 Northwind 샘플 데이터베이스 및 SQL Server Express LocalDB를 사용 합니다.

1. SQL Server Express LocalDB가 없는 경우 설치에서 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express), 또는 합니다 **Visual Studio 설치 관리자**합니다. Visual Studio 설치 관리자를 SQL Server Express LocalDB의 일부로 설치할 수 있습니다 합니다 **.NET 데스크톱 개발** 워크 로드 또는 개별 구성 요소입니다.

2. 다음이 단계를 수행 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

    1. Visual Studio에서 엽니다는 **SQL Server 개체 탐색기** 창입니다. (SQL Server 개체 탐색기의 일부로 설치 되는 **데이터 저장소 및 처리** Visual Studio 설치 관리자에서 작업 합니다.) 확장 된 **SQL Server** 노드. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 선택 **새 쿼리**합니다.

       쿼리 편집기 창이 열립니다.

    2. 복사 합니다 [Northwind Transact SQL 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 클립보드에 있습니다. 이 T-SQL 스크립트부터에서 Northwind 데이터베이스를 만들고 데이터로 채웁니다.

    3. T-SQL 스크립트, 쿼리 편집기에 붙여넣고 선택한 합니다 **Execute** 단추입니다.

       짧은 시간 후 쿼리 실행이 완료 하 고 Northwind 데이터베이스 생성 됩니다.

## <a name="create-a-windows-forms-application"></a>Windows Forms 애플리케이션 만들기

첫 번째 단계를 만드는 것을 **Windows Forms 응용 프로그램**합니다.

1. Visual Studio에서에 **파일** 메뉴에서 **새로 만들기** > **프로젝트**합니다.

2. 확장 **Visual C#** 하거나 **Visual Basic** 왼쪽 창에서 선택한 **Windows Desktop**합니다.

3. 가운데 창에서 선택 합니다 **Windows Forms 앱** 형식 프로젝션 합니다.

4. 프로젝트 이름을 **SavingDataInATransactionWalkthrough**를 선택한 후 **확인**합니다.

     **SavingDataInATransactionWalkthrough** 프로젝트가 만들어져 **솔루션 탐색기**에 추가됩니다.

## <a name="create-a-database-data-source"></a>데이터베이스 데이터 원본 만들기

이 단계에서는 합니다 **데이터 소스 구성 마법사** 기반으로 데이터 원본을 만들려면 합니다 `Customers` 및 `Orders` Northwind 샘플 데이터베이스의 테이블입니다.

1. 열려는 **데이터 원본** 창에는 **데이터** 메뉴를 선택 **데이터 소스 표시**.

2. **데이터 원본** 창에서 **새 데이터 원본 추가**를 선택하여 **데이터 원본 구성 마법사**를 시작합니다.

3. 에 **데이터 소스 형식 선택** 화면에서 **데이터베이스**를 선택한 후 **다음**합니다.

4. 에 **데이터 연결 선택** 화면 작업 중 하나를 수행 합니다.

    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

         또는

    - **새 연결**을 선택하여 **연결 추가/수정** 대화 상자를 시작하고 Northwind 데이터베이스에 대한 연결을 만듭니다.

5. 데이터베이스에서 암호를 요구 하는 경우 중요 한 데이터를 포함 하 여 선택한 옵션을 선택 **다음**합니다.

6. 에 **응용 프로그램 구성 파일에 연결 문자열을 저장** 화면에서 **다음**합니다.

7. 에 **데이터베이스 개체 선택** 화면에서 확장 된 **테이블** 노드.

8. 선택 된 `Customers` 하 고 `Orders` 테이블을 선택한 후 **완료**합니다.

     **NorthwindDataSet**가 프로젝트에 추가되고 `Customers` 및 `Orders` 테이블이 **데이터 원본** 창에 나타납니다.

## <a name="add-controls-to-the-form"></a>폼에 컨트롤 추가

**데이터 원본** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만들 수 있습니다.

1. 에 **데이터 원본** 창 확장 합니다 **고객** 노드.

2. 주 **Customers** 노드를 **데이터 원본** 창에서 **Form1**으로 끌어서 놓습니다.

   <xref:System.Windows.Forms.DataGridView> 컨트롤과 레코드 탐색에 사용되는 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>가 폼에 나타납니다. A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)를 `CustomersTableAdapter`를 <xref:System.Windows.Forms.BindingSource>, 및 <xref:System.Windows.Forms.BindingNavigator> 구성 요소 트레이에 나타납니다.

3. 관련 끌어 **주문** 노드 (주 **주문** 아니라 노드 아래의 관련된 자식 테이블 노드를 **팩스** 열)를 폼은  **CustomersDataGridView**합니다.

   <xref:System.Windows.Forms.DataGridView>가 폼에 나타납니다. `OrdersTableAdapter` 고 <xref:System.Windows.Forms.BindingSource> 구성 요소 트레이에 나타납니다.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>System.Transactions 어셈블리에 대 한 참조를 추가 합니다.

트랜잭션은 <xref:System.Transactions> 네임스페이스를 사용합니다. system.transactions 어셈블리에 대한 프로젝트 참조는 기본적으로 추가되어 있지 않으므로 수동으로 추가해야 합니다.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>System.Transactions DLL 파일에 대한 참조를 추가하려면

1. **프로젝트** 메뉴에서 **참조 추가**를 선택합니다.

2. 선택 **System.Transactions** (에 **.NET** 탭)을 선택한 후 **확인**합니다.

     **System.Transactions**에 대한 참조가 프로젝트에 추가됩니다.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>BindingNavigator의 SaveItem 단추에 코드를 수정 합니다.

폼에 놓은 첫 번째 테이블에 대 한 코드가 기본적으로 추가 됩니다는 `click` 이벤트 저장 단추를 <xref:System.Windows.Forms.BindingNavigator>입니다. 추가 테이블을 업데이트하려면 코드를 수동으로 추가해야 합니다. 이 연습에서는 리팩터링 기존 저장 코드 저장 단추의 클릭 이벤트 처리기입니다. 행 추가 또는 삭제 해야 하는 여부에 따라 특정 업데이트 기능을 제공 하는 몇 가지 더 많은 메서드를 만들 수도 있습니다.

### <a name="to-modify-the-auto-generated-save-code"></a>자동으로 생성된 저장 코드를 수정하려면

1. 선택 합니다 **저장할** 단추를 **CustomersBindingNavigator** (플로피 디스크 아이콘이 있는 단추).

2. `CustomersBindingNavigatorSaveItem_Click` 메서드를 다음 코드로 바꿉니다.

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

관련 데이터의 변경을 조정하는 순서는 다음과 같습니다.

- 자식 레코드를 삭제 합니다. (이 경우 레코드를 삭제 합니다 `Orders` 테이블입니다.)

- 부모 레코드를 삭제 합니다. (이 경우 레코드를 삭제 합니다 `Customers` 테이블입니다.)

- 부모 레코드를 삽입 합니다. (이 경우에 레코드를 삽입 합니다 `Customers` 테이블입니다.)

- 자식 레코드를 삽입 합니다. (이 경우에 레코드를 삽입 합니다 `Orders` 테이블입니다.)

### <a name="to-delete-existing-orders"></a>기존 주문을 삭제하려면

- 다음 `DeleteOrders` 메서드를 **Form1**에 추가합니다.

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>기존 고객을 삭제하려면

- 다음 `DeleteCustomers` 메서드를 **Form1**에 추가합니다.

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>새 고객을 추가하려면

- 다음 `AddNewCustomers` 메서드를 **Form1**에 추가합니다.

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>새 주문을 추가하려면

- 다음 `AddNewOrders` 메서드를 **Form1**에 추가합니다.

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>애플리케이션 실행

**F5** 키를 눌러 응용 프로그램을 실행합니다.

## <a name="see-also"></a>참고자료

- [방법: 트랜잭션을 사용하여 데이터 저장](../data-tools/save-data-by-using-a-transaction.md)
- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)