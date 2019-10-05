---
title: 트랜잭션에 데이터 저장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 08480e46ab492acb1c7ab10c8514897721708aba
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692463"
---
# <a name="save-data-in-a-transaction"></a>트랜잭션에 데이터 저장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 사용 하 여 트랜잭션에서 데이터를 저장 하는 방법에 설명 합니다 <xref:System.Transactions> 네임 스페이스입니다. 이 예에서는 Northwind 샘플 데이터베이스의 `Customers` 및 `Orders` 테이블을 사용합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 진행하려면 Northwind 샘플 데이터베이스에 액세스해야 합니다.
  
## <a name="create-a-windows-application"></a>Windows 응용 프로그램 만들기  
 첫 번째 단계를 만드는 것을 **Windows 응용 프로그램**합니다.  
  
#### <a name="to-create-the-new-windows-project"></a>새 Windows 프로젝트를 만들려면  
  
1. Visual Studio에서에 **파일** 메뉴에서 새 **프로젝트**합니다.  
  
2. 프로젝트 이름을 **SavingDataInATransactionWalkthrough**합니다.  
  
3. 선택 **Windows 응용 프로그램**를 선택한 후 **확인**합니다. 자세한 내용은 [클라이언트 응용 프로그램](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)합니다.  
  
     **SavingDataInATransactionWalkthrough** 프로젝트가 만들어져 **솔루션 탐색기**에 추가됩니다.  
  
## <a name="create-a-database-data-source"></a>데이터베이스 데이터 원본 만들기  
 이 단계에서는 합니다 [데이터 소스 구성 마법사](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) 기반으로 데이터 원본을 만들려면 합니다 `Customers` 및 `Orders` Northwind 샘플 데이터베이스의 테이블입니다.  
  
#### <a name="to-create-the-data-source"></a>데이터 소스를 만들려면  
  
1. 에 **데이터** 메뉴에서**데이터 소스 표시**합니다.  
  
2. **데이터 원본** 창에서 **새 데이터 원본 추가**를 선택하여 **데이터 원본 구성 마법사**를 시작합니다.  
  
3. 에 **데이터 소스 형식 선택**화면에서 **데이터베이스**를 선택한 후 **다음**합니다.  
  
4. 에 **데이터 연결 선택**화면 작업 중 하나를 수행 합니다.  
  
    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.  
  
         또는  
  
    - **새 연결**을 선택하여 **연결 추가/수정** 대화 상자를 시작하고 Northwind 데이터베이스에 대한 연결을 만듭니다.  
  
5. 데이터베이스에서 암호를 요구 하는 경우 중요 한 데이터를 포함 하 여 선택한 옵션을 선택 **다음**합니다.  
  
6. 에 **응용 프로그램 구성 파일에 연결 문자열을 저장** 화면에서 **다음**합니다.  
  
7. 에 **데이터베이스 개체 선택** 화면에서 확장 된 **테이블** 노드.  
  
8. 선택 된 `Customers` 하 고 `Orders` 테이블을 선택한 후 **완료**합니다.  
  
     **NorthwindDataSet**가 프로젝트에 추가되고 `Customers` 및 `Orders` 테이블이 **데이터 원본** 창에 나타납니다.  
  
## <a name="addcontrols-to-the-form"></a>폼에 Addcontrols  
 **데이터 원본** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만들 수 있습니다.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Windows form의 컨트롤에 바인딩된 데이터를 만들려면  
  
- 에 **데이터 원본** 창 확장 합니다 **고객** 노드.  
  
- 주 **Customers** 노드를 **데이터 원본** 창에서 **Form1**으로 끌어서 놓습니다.  
  
     <xref:System.Windows.Forms.DataGridView> 컨트롤과 레코드 탐색에 사용되는 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>가 폼에 나타납니다. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> 및 <xref:System.Windows.Forms.BindingNavigator>가 구성 요소 트레이에 나타납니다.  
  
- 관련 끌어 **주문** 노드 (주 **주문** 아니라 노드 아래의 관련된 자식 테이블 노드를 **팩스** 열)를 폼은  **CustomersDataGridView**합니다.  
  
     <xref:System.Windows.Forms.DataGridView>가 폼에 나타납니다. OrdersTableAdapter 및 <xref:System.Windows.Forms.BindingSource> 구성 요소 트레이에 나타납니다.  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>System.Transactions 어셈블리에 대 한 참조를 추가 합니다.  
 트랜잭션은 <xref:System.Transactions> 네임스페이스를 사용합니다. System.Transactions 어셈블리에 대 한 프로젝트 참조를 수동으로 추가 해야 하므로 기본적으로 추가 되지 않습니다.  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>System.Transactions DLL 파일에 대한 참조를 추가하려면  
  
1. 에 **프로젝트** 메뉴에서**참조 추가**합니다.  
  
2. 선택 **System.Transactions**(에 **.NET** 탭)을 선택한 후 **확인**합니다.  
  
     **System.Transactions**에 대한 참조가 프로젝트에 추가됩니다.  
  
## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>BindingNavigator의 SaveItem 단추 Modifythe 코드  
 폼에 놓은 첫 번째 테이블에 대 한 코드가 기본적으로 추가 됩니다는 `click` 이벤트 저장 단추를 <xref:System.Windows.Forms.BindingNavigator>입니다. 추가 테이블을 업데이트하려면 코드를 수동으로 추가해야 합니다. 이 연습에서는 리팩터링 기존 저장 코드 저장 단추의 클릭 이벤트 처리기입니다. 행 추가 또는 삭제 해야 하는 여부에 따라 특정 업데이트 기능을 제공 하는 몇 가지 더 많은 메서드를 만들 수도 있습니다.  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>자동으로 생성된 저장 코드를 수정하려면  
  
1. 선택 합니다 **저장할** 단추를 **CustomersBindingNavigator** (플로피 디스크 아이콘이 있는 단추).  
  
2. `CustomersBindingNavigatorSaveItem_Click` 메서드를 다음 코드로 바꿉니다.  
  
    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]  
  
   관련 데이터의 변경을 조정하는 순서는 다음과 같습니다.  
  
- 자식 레코드를 삭제 합니다. (이 경우 레코드를 삭제 합니다 `Orders` 테이블입니다.)  
  
- 부모 레코드를 삭제 합니다. (이 경우 레코드를 삭제 합니다 `Customers` 테이블입니다.)  
  
- 부모 레코드를 삽입 합니다. (이 경우에 레코드를 삽입 합니다 `Customers` 테이블입니다.)  
  
- 자식 레코드를 삽입 합니다. (이 경우에 레코드를 삽입 합니다 `Orders` 테이블입니다.)  
  
#### <a name="to-delete-existing-orders"></a>기존 주문을 삭제하려면  
  
- 다음 `DeleteOrders` 메서드를 **Form1**에 추가합니다.  
  
     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]  
  
#### <a name="to-delete-existing-customers"></a>기존 고객을 삭제하려면  
  
- 다음 `DeleteCustomers` 메서드를 **Form1**에 추가합니다.  
  
     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]  
  
#### <a name="to-add-new-customers"></a>새 고객을 추가하려면  
  
- 다음 `AddNewCustomers` 메서드를 **Form1**에 추가합니다.  
  
     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]  
  
#### <a name="to-add-new-orders"></a>새 주문을 추가하려면  
  
- 다음 `AddNewOrders` 메서드를 **Form1**에 추가합니다.  
  
     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]  
  
## <a name="run-the-application"></a>애플리케이션 실행  
  
#### <a name="to-run-the-application"></a>애플리케이션을 실행하려면  
  
- 선택 **F5** 응용 프로그램을 실행 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
