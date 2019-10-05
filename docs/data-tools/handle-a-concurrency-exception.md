---
title: 동시성 예외 처리
ms.date: 09/11/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a8e14a53719d4913bcc04bcb2b702ca4ec4a8c55
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62566744"
---
# <a name="handle-a-concurrency-exception"></a>동시성 예외 처리

동시성 예외 (<xref:System.Data.DBConcurrencyException?displayProperty=fullName>)는 두 사용자가 동시에 데이터베이스에서 동일한 데이터를 변경 하려고 할 때 발생 합니다. 이 연습에서는 catch 하는 방법을 보여 주는 Windows 응용 프로그램을 만든를 <xref:System.Data.DBConcurrencyException>오류를 발생 시킨 행 찾아 처리 하는 방법에 대 한 전략에 알아봅니다.

이 연습에서는 다음 프로세스를 안내합니다.

1. 새 **Windows Forms 애플리케이션** 프로젝트를 만듭니다.

2. Northwind Customers 테이블을 기반으로 새 데이터 집합을 만듭니다.

3. 양식 만들기는 <xref:System.Windows.Forms.DataGridView> 데이터를 표시 합니다.

4. Northwind 데이터베이스의 Customers 테이블에서 데이터를 사용 하 여 데이터 집합을 입력 합니다.

5. 사용 합니다 **테이블 데이터 표시** 기능 **서버 탐색기** Customers 테이블의 데이터에 액세스 하 여 레코드를 변경 합니다.

6. 다른 값으로 동일한 레코드를 변경, 데이터 집합을 업데이트 하 고 동시성 오류가 발생 하는 데이터베이스에 변경 내용 쓰기 시도 합니다.

7. 오류를 catch 하, 사용자가 계속를 데이터베이스를 업데이트할지 여부를 결정할 수 있도록 레코드의 다른 버전을 표시 또는 업데이트 작업을 취소 합니다.

## <a name="prerequisites"></a>전제 조건

이 연습에서는 Northwind 샘플 데이터베이스 및 SQL Server Express LocalDB를 사용 합니다.

1. SQL Server Express LocalDB가 없는 경우 설치에서 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express), 또는 합니다 **Visual Studio 설치 관리자**합니다. 에 **Visual Studio 설치 관리자**의 일부로 SQL Server Express LocalDB를 설치할 수 있습니다는 **데이터 저장 및 처리** 워크 로드 또는 개별 구성 요소로 합니다.

2. 다음이 단계를 수행 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

    1. Visual Studio에서 엽니다는 **SQL Server 개체 탐색기** 창입니다. (SQL Server 개체 탐색기의 일부로 설치 되는 **데이터 저장소 및 처리** Visual Studio 설치 관리자에서 작업 합니다.) 확장 된 **SQL Server** 노드. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 선택 **새 쿼리**합니다.

       쿼리 편집기 창이 열립니다.

    2. 복사 합니다 [Northwind Transact SQL 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 클립보드에 있습니다. 이 T-SQL 스크립트부터에서 Northwind 데이터베이스를 만들고 데이터로 채웁니다.

    3. T-SQL 스크립트, 쿼리 편집기에 붙여넣고 선택한 합니다 **Execute** 단추입니다.

       짧은 시간 후 쿼리 실행이 완료 하 고 Northwind 데이터베이스 생성 됩니다.

## <a name="create-a-new-project"></a>새 프로젝트 만들기

새 Windows Forms 응용 프로그램을 만들어 시작 합니다.

1. Visual Studio에서에 **파일** 메뉴에서 **새로 만들기** > **프로젝트**합니다.

2. 확장 **Visual C#** 하거나 **Visual Basic** 왼쪽 창에서 선택한 **Windows Desktop**합니다.

3. 가운데 창에서 선택 합니다 **Windows Forms 앱** 형식 프로젝션 합니다.

4. 프로젝트 이름을 **ConcurrencyWalkthrough**를 선택한 후 **확인**합니다.

     합니다 **ConcurrencyWalkthrough** 프로젝트에 추가한 생성 **솔루션 탐색기**, 디자이너에서 새 양식을 엽니다.

## <a name="create-the-northwind-dataset"></a>Northwind 데이터 집합을 만들려면

다음으로 명명 된 데이터 집합을 만듭니다 **NorthwindDataSet**:

1. 에 **데이터** 메뉴 선택 **새 데이터 소스 추가**합니다.

   데이터 원본 구성 마법사가 열립니다.

2. 에 **데이터 소스 형식 선택** 화면에서 **데이터베이스**합니다.

   ![Visual Studio에서 데이터 소스 구성 마법사](media/data-source-configuration-wizard.png)

3. 사용 가능한 연결 목록에서 Northwind 샘플 데이터베이스에 대 한 연결을 선택 합니다. 연결 된 연결 목록에서 사용할 수 없는 경우 선택 **새 연결**합니다.

    > [!NOTE]
    > 로컬 데이터베이스 파일에 연결 하는 경우 선택 **No** 프로젝트에 파일을 추가 하려는 설정 하려는 경우 메시지가 표시 되 면 합니다.

4. 에 **응용 프로그램 구성 파일에 연결 문자열 저장** 화면에서 **다음**합니다.

5. 확장을 **테이블** 노드를 선택 합니다 **고객** 테이블입니다. 데이터 집합에 대 한 기본 이름이 있어야 **NorthwindDataSet**합니다.

6. 선택 **완료** 데이터 집합 프로젝트에 추가 합니다.

## <a name="create-a-data-bound-datagridview-control"></a>데이터 바인딩된 DataGridView 컨트롤 만들기

만든이 섹션에서는 <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> 끌어서를 **고객** 에서 항목을 **데이터 원본** 창에서 Windows 폼으로 합니다.

1. 열려는 **데이터 원본** 창에는 **데이터** 메뉴에서 선택 **데이터 소스 표시**.

2. 에 **데이터 원본** 창 확장 합니다 **NorthwindDataSet** 노드를 선택한 후는 **고객** 테이블.

3. 테이블 노드의 아래쪽 화살표를 선택 하 고 선택한 **DataGridView** 드롭 다운 목록에서.

4. 폼의 빈 영역으로 테이블을 끕니다.

     <xref:System.Windows.Forms.DataGridView> 라는 컨트롤 **CustomersDataGridView**, 및 <xref:System.Windows.Forms.BindingNavigator> 라는 **CustomersBindingNavigator**에 바인딩된 폼에 추가 되는 <xref:System.Windows.Forms.BindingSource>합니다. 차례로 NorthwindDataSet의 Customers 테이블에 바인딩된 인이 있습니다.

## <a name="test-the-form"></a>형식 테스트

이제 폼이이 지점까지 예상 대로 작동 하는지 확인을 테스트할 수 있습니다.

1. 선택 **F5** 응용 프로그램을 실행 합니다.

     폼이 표시는 <xref:System.Windows.Forms.DataGridView> 컨트롤이 있는 Customers 테이블의 데이터로 채워집니다.

2. 에 **디버그** 메뉴에서 **디버깅 중지**합니다.

## <a name="handle-concurrency-errors"></a>동시성 오류 처리

오류를 처리 하는 방법을 응용 프로그램을 제어 하는 특정 비즈니스 규칙에 따라 달라 집니다. 이 연습에서는 동시성 오류를 처리 하는 방법에 대 한 예를 들어 다음 전략을 사용 합니다.

응용 프로그램 레코드의 세 가지 버전을 사용 하 여 사용자를 제공합니다.

- 데이터베이스의 현재 레코드

- 데이터 집합에 로드 된 원본 레코드

- 데이터 집합에서 제안 된 변경

그러면 사용자는 제안된 된 버전을 사용 하 여 데이터베이스를 덮어쓸 또는 업데이트 작업을 취소 및 데이터베이스의 새 값을 사용 하 여 데이터 집합을 새로 고칠 수 있습니다.

### <a name="to-enable-the-handling-of-concurrency-errors"></a>동시성 오류 처리를 사용 하도록 설정 하려면

1. 사용자 지정 오류 처리기를 만듭니다.

2. 사용자에 게 선택 항목을 표시 합니다.

3. 사용자의 응답을 처리 합니다.

4. 업데이트를 다시 하거나 데이터 집합의 데이터를 다시 설정 합니다.

### <a name="add-code-to-handle-the-concurrency-exception"></a>동시성 예외를 처리 하는 코드를 추가 합니다.

업데이트를 수행 하려고 하면 예외가 발생 하는 경우 일반적으로 발생된 된 예외에서 제공 하는 정보를 사용 하 여 작업을 수행 하려고 합니다. 이 섹션에서는 데이터베이스를 업데이트 하는 코드를 추가 합니다. 또한 처리 된 <xref:System.Data.DBConcurrencyException> 는 발생할 수 있는 다른 예외와 합니다.

> [!NOTE]
> 합니다 `CreateMessage` 고 `ProcessDialogResults` 연습의 뒷부분에서는 메서드가 추가 됩니다.

1. 아래 다음 코드를 추가 합니다 `Form1_Load` 메서드:

   [!code-csharp[VbRaddataConcurrency#1](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_1.cs)]
   [!code-vb[VbRaddataConcurrency#1](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_1.vb)]

2. 대체는 `CustomersBindingNavigatorSaveItem_Click` 메서드를 호출 하는 `UpdateDatabase` 메서드를 다음과 같이 표시 됩니다:

   [!code-csharp[VbRaddataConcurrency#2](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_2.cs)]
   [!code-vb[VbRaddataConcurrency#2](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_2.vb)]

### <a name="display-choices-to-the-user"></a>사용자에 게 표시 선택

방금 코드 호출을 작성 합니다 `CreateMessage` 사용자에 게 오류 정보를 표시 하는 프로시저입니다. 이 연습에서는 사용자에 게 서로 다른 버전의 레코드를 표시 하는 메시지 상자를 사용 합니다. 이 레코드 변경 내용으로 덮어쓰거나 편집을 취소 하도록 선택할 수 있습니다. 응답에 전달 되 면 메시지 상자에 있는 (단추 클릭) 하는 옵션을 선택 합니다 `ProcessDialogResult` 메서드.

다음 코드를 추가 하 여 메시지를 만들 합니다 **코드 편집기**합니다. 아래이 코드를 입력 합니다 `UpdateDatabase` 메서드:

[!code-csharp[VbRaddataConcurrency#4](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_3.cs)]
[!code-vb[VbRaddataConcurrency#4](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_3.vb)]

### <a name="process-the-users-response"></a>사용자의 응답 처리

메시지 상자에 대 한 사용자의 응답을 처리 하는 코드를 해야 합니다. 제안된 된 변경으로 데이터베이스의 현재 레코드를 덮어쓸 또는 로컬 변경 내용을 취소 하 고 현재 데이터베이스에 있는 레코드를 사용 하 여 데이터 테이블을 새로 고칠를 선택할 수 있습니다. 사용자가 선택 **예**의 <xref:System.Data.DataTable.Merge%2A> 메서드를 호출 합니다 *preserveChanges* 인수와 함께 **true**합니다. 이렇게 하면 될 레코드의 원래 버전 데이터베이스의 레코드와 일치 하므로 업데이트 하려고 합니다.

이전 섹션에서 추가한 코드 아래에 다음 코드를 추가 합니다.

[!code-csharp[VbRaddataConcurrency#3](../data-tools/codesnippet/CSharp/handle-a-concurrency-exception_4.cs)]
[!code-vb[VbRaddataConcurrency#3](../data-tools/codesnippet/VisualBasic/handle-a-concurrency-exception_4.vb)]

## <a name="test-the-form"></a>형식 테스트

이제 예상 대로 작동 되도록 폼을 테스트할 수 있습니다. 동시성 위반을 시뮬레이트하기 위해 NorthwindDataSet를 채운 후 데이터베이스의 데이터를 변경 합니다.

1. 선택 **F5** 응용 프로그램을 실행 합니다.

2. 폼에 나타납니다. 계속 해 서 실행 후 Visual Studio IDE로 전환 합니다.

3. 에 **뷰** 메뉴 선택 **서버 탐색기**합니다.

4. **서버 탐색기**, 응용 프로그램은 사용 및 확장 한 다음 연결을 확장 합니다 **테이블** 노드.

5. 마우스 오른쪽 단추로 클릭 합니다 **고객이** 테이블을 선택한 후 **테이블 데이터 표시**합니다.

6. 첫 번째 레코드에서 (**ALFKI**)을 변경 **ContactName** 하 **Maria Anders2**합니다.

    > [!NOTE]
    > 변경 내용을 커밋하려면 다른 행으로 이동 합니다.

7. ConcurrencyWalkthrough의 실행 중인 양식으로 전환 합니다.

8. 양식의 첫 번째 레코드에서 (**ALFKI**)을 변경 **ContactName** 하 **Maria Anders1**합니다.

9. **저장** 단추를 선택합니다.

     동시성 오류가 발생 하 고 메시지 상자가 나타납니다.

   선택 **No** 업데이트를 취소 하 고 현재 데이터베이스에 있는 값을 사용 하 여 데이터 집합을 업데이트 합니다. 선택 **예** 제안 된 값이 데이터베이스에 기록 합니다.

## <a name="see-also"></a>참고자료

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)