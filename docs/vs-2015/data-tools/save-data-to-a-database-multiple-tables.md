---
title: 데이터베이스 (여러 테이블)에 데이터를 저장 합니다. | Microsoft Docs
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 132aa0f37cc63e6afe2eff61a6d0f6dec5b200b5
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692442"
---
# <a name="save-data-to-a-database-multiple-tables"></a>데이터베이스에 데이터 저장(여러 테이블)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

애플리케이션 개발에서 가장 일반적인 시나리오는 Windows 애플리케이션의 폼에 데이터를 표시하고 데이터를 편집한 다음 업데이트된 데이터를 데이터베이스로 다시 보내는 것입니다. 이 연습에서는 두 관련 테이블의 데이터를 표시하는 폼을 만들고, 레코드를 편집한 다음 변경 내용을 데이터베이스에 다시 저장하는 방법을 보여줍니다. 이 예에서는 Northwind 샘플 데이터베이스의 `Customers` 및 `Orders` 테이블을 사용합니다.  
  
 TableAdapter의 `Update` 메서드를 호출하여 애플리케이션의 데이터를 데이터베이스에 다시 저장할 수 있습니다. 테이블을 끌면 합니다 **데이터 원본** 창에서 폼에 데이터를 저장 하는 데 필요한 코드를 자동으로 추가 됩니다. 이 코드를 수동으로 추가 해야 하는 추가 테이블이 있는 폼에 추가 됩니다. 이 연습에서는 둘 이상의 테이블에서 업데이트를 저장하는 코드를 추가하는 방법을 보여줍니다.  
  
> [!NOTE]
> 대화 상자와 메뉴 명령은 활성 설정 또는 사용 중인 버전에 따라 도움말에서 설명 하는 것에서 다 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조하세요.  
  
 이 연습에서 설명하는 작업은 다음과 같습니다.  
  
- 새로 만들 **Windows 응용 프로그램** 프로젝트입니다.  
  
- 만들기 및 사용 하 여 응용 프로그램에서 데이터 원본을 구성 합니다 [데이터 소스 구성 마법사](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)합니다.  
  
- 에 있는 항목의 컨트롤을 설정 합니다 [데이터 소스 창](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)합니다.  
  
- **데이터 원본** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만듭니다.  
  
- 데이터 집합의 각 테이블에서 몇 가지 레코드를 수정 합니다.  
  
- 데이터 세트의 업데이트된 데이터를 데이터베이스로 다시 보내도록 코드를 수정합니다.  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 완료하려면 다음 사항이 필요합니다.  
  
- Northwind 샘플 데이터베이스에 대한 액세스.
  
## <a name="create-the-windows-application"></a>Windows 응용 프로그램 만들기  
 첫 번째 단계를 만드는 것을 **Windows 응용 프로그램**합니다. 이 단계 중에 선택 사항 이므로 프로젝트에 이름을 할당 하지만 이름을 지정 하겠습니다 것을 나중에 저장할 계획 이므로 합니다.  
  
#### <a name="to-create-the-new-windows-application-project"></a>새 Windows 응용 프로그램 프로젝트를 만들려면  
  
1. 에 **파일** 메뉴에서 새 프로젝트를 만듭니다.  
  
2. 프로젝트 이름을 `UpdateMultipleTablesWalkthrough`로 지정합니다.  
  
3. 선택 **Windows 응용 프로그램**를 선택한 후 **확인**합니다. 자세한 내용은 [클라이언트 응용 프로그램](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)합니다.  
  
     **UpdateMultipleTablesWalkthrough** 프로젝트가 만들어져 **솔루션 탐색기**에 추가됩니다.  
  
## <a name="create-the-data-source"></a>데이터 원본 만들기  
 이 단계에서는 **데이터 원본 구성 마법사**를 사용하여 Northwind 데이터베이스에서 데이터 원본을 만듭니다. 연결을 만들려면 Northwind 샘플 데이터베이스에 액세스해야 합니다.
  
#### <a name="to-create-the-data-source"></a>데이터 소스를 만들려면  
  
1. 에 **데이터** 메뉴에서**데이터 소스 표시**합니다.  
  
2. 에 **데이터 원본** 창에서**새 데이터 소스 추가** 시작 하는 **데이터 소스 구성 마법사**합니다.  
  
3. 에 **데이터 소스 형식 선택**화면에서 **데이터베이스**를 선택한 후 **다음**합니다.  
  
4. 에 **데이터 연결 선택**화면 작업 중 하나를 수행 합니다.  
  
    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.  
  
         또는  
  
    - **새 연결**을 선택하여 **연결 추가 또는 수정** 대화 상자를 엽니다.  
  
5. 데이터베이스에서 암호를 요구 하는 경우 중요 한 데이터를 포함 하 여 선택한 옵션을 선택 **다음**합니다.  
  
6. 에 **응용 프로그램 구성 파일에 연결 문자열을 저장**를 선택 **다음**합니다.  
  
7. 에 **데이터베이스 개체 선택**화면에서 확장 된 **테이블** 노드.  
  
8. 선택 합니다 **고객** 하 고 **주문** 테이블을 선택한 후 **마침**.  
  
     **NorthwindDataSet**가 프로젝트에 추가되고 테이블이 **데이터 원본** 창에 나타납니다.  
  
## <a name="set-the-controls-to-be-created"></a>만들 컨트롤 설정  
 이 연습에서는 데이터에는 `Customers` 테이블은는 **세부 정보** 레이아웃 데이터를 개별 컨트롤에에서 표시 되는 위치입니다. 데이터를 `Orders` 테이블은는 **표** 레이아웃에 표시 되는 <xref:System.Windows.Forms.DataGridView> 컨트롤.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>데이터 소스 창에서 항목에 대한 삭제 유형을 설정하려면  
  
1. 에 **데이터 원본** 창 확장 합니다 **고객** 노드.  
  
2. 에 **고객** 노드를 선택 **세부 정보** 의 컨트롤을 변경 하 고 컨트롤 목록에서를 **고객** 테이블을 개별 컨트롤로 합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)합니다.  
  
## <a name="create-the-data-bound-form"></a>데이터 바인딩된 폼을 만들려면  
 **데이터 원본** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만들 수 있습니다.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>폼에서 데이터 바인딩된 컨트롤을 만들려면  
  
1. 주 **Customers** 노드를 **데이터 원본** 창에서 **Form1**으로 끌어서 놓습니다.  
  
     설명 레이블이 있는 데이터 바인딩된 컨트롤이 레코드 탐색을 위한 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>와 함께 폼에 나타납니다. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> 및 <xref:System.Windows.Forms.BindingNavigator>가 구성 요소 트레이에 나타납니다.  
  
2. 관련 **Orders** 노드를 **데이터 원본** 창에서 **Form1**으로 끌어 옵니다.  
  
    > [!NOTE]
    > **Fax** 열 아래에 있는 관련 **Orders** 노드는 **Customers** 노드의 자식 노드입니다.  
  
     <xref:System.Windows.Forms.DataGridView> 컨트롤과 레코드 탐색에 사용되는 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>가 폼에 나타납니다. OrdersTableAdapter 및 <xref:System.Windows.Forms.BindingSource> 구성 요소 트레이에 나타납니다.  
  
## <a name="addcode-to-update-the-database"></a>데이터베이스를 업데이트 하려면 Addcode  
 **Customers** 및 **Orders** TableAdapters의 `Update` 메서드를 호출하여 데이터베이스를 업데이트할 수 있습니다. 기본적으로 대 한 이벤트 처리기를 **저장** 단추를<xref:System.Windows.Forms.BindingNavigator> 데이터베이스로 업데이트를 보내는 폼의 코드에 추가 됩니다. 이 절차에서는 올바른 순서로 업데이트를 보내는 코드를 수정 합니다. 이 참조 무결성 오류 발생 가능성을 제거 합니다. 또한 이 코드는 try-catch 블록에서 업데이트 호출을 래핑하여 오류 처리를 구현합니다. 애플리케이션의 요구 사항에 맞게 코드를 수정할 수 있습니다.  
  
> [!NOTE]
> 이해를 돕기 위해이 연습에는 트랜잭션을 사용 하지 않습니다. 그러나 두 업데이트 하는 경우 테이블 관련 트랜잭션 내에서 모든 업데이트 논리를 포함 합니다. 트랜잭션은 모든 변경 내용이 커밋되기 전에 모든 관련된 변경 내용이 데이터베이스에는 성공적으로 만드는 프로세스입니다. 자세한 내용은 [트랜잭션 및 동시성](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b)합니다.  
  
#### <a name="to-add-update-logic-to-the-application"></a>애플리케이션에 업데이트 논리를 추가하려면  
  
1. 선택 된 **저장** 단추를 <xref:System.Windows.Forms.BindingNavigator>입니다. 코드 편집기에 열립니다는 `bindingNavigatorSaveItem_Click` 이벤트 처리기입니다.  
  
2. 관련 TableAdapter의 `Update` 메서드를 호출하도록 이벤트 처리기의 코드를 바꿉니다. 다음 코드는 먼저 각 <xref:System.Data.DataRowState>(<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> 및 <xref:System.Data.DataRowState>)에 대해 업데이트된 정보를 저장할 3개 임시 데이터 테이블을 만듭니다. 그런 다음 업데이트는 올바른 순서로 실행 됩니다. 이 코드는 다음과 같습니다.  
  
     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]  
  
## <a name="test-the-application"></a>애플리케이션 테스트  
  
#### <a name="to-test-the-application"></a>애플리케이션을 테스트하려면  
  
1. 선택 **F5**합니다.  
  
2. 각 테이블에 포함된 레코드 하나 이상의 데이터를 변경해 봅니다.  
  
3. **저장** 단추를 선택합니다.  
  
4. 데이터베이스의 값을 점검하여 변경 내용이 저장되었는지 확인합니다.  
  
## <a name="next-steps"></a>다음 단계  
 응용 프로그램 요구 사항에 따라 일부의 단계가 있습니다 Windows 응용 프로그램에서 데이터 바인딩된 폼을 만든 후 수행 하는 것이 좋습니다. 이 연습에서 보완할 수 있는 사항은 다음과 같습니다.  
  
- 폼에 검색 기능을 추가합니다. 자세한 내용은 [방법: 매개 변수가 있는 쿼리는 Windows Forms 응용 프로그램 추가](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416)합니다.  
  
- 데이터 소스를 편집하여 데이터베이스 개체를 추가하거나 편집합니다. 자세한 내용은 [방법: 데이터 집합 편집](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
