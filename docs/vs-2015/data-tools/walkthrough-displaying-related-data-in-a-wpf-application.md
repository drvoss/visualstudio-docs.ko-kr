---
title: '연습: WPF 응용 프로그램에서 관련된 데이터 표시 | Microsoft Docs'
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
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 560852fc25a3e00134e4ed8b6bd06205248b208d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65688418"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>연습: WPF 응용 프로그램에서 관련된 데이터 표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 부모/자식 관계가 있는 데이터베이스 테이블에서 데이터를 표시 하는 WPF 응용 프로그램을 만들게 됩니다. 데이터는 엔터티 데이터 모델의 엔터티에 캡슐화 됩니다. 부모 엔터티가 orders의 집합에 대 한 개요 정보를 포함합니다. 이 엔터티의 각 속성은 응용 프로그램에서 다른 컨트롤에 바인딩됩니다. 자식 엔터티는 각 주문에 대 한 세부 정보를 포함합니다. 이 데이터 집합에 바인딩되는 <xref:System.Windows.Controls.DataGrid> 제어 합니다.  
  
 이 연습에서는 다음 작업을 수행합니다.  
  
- WPF 응용 프로그램 및 AdventureWorksLT 샘플 데이터베이스의 데이터에서 생성 되는 엔터티 데이터 모델을 만듭니다.  
  
- 주문 집합에 대 한 개요 정보를 표시 하는 데이터 바인딩된 컨트롤의 집합을 만드는 중입니다. 부모 엔터티를 끌어 컨트롤을 만든 합니다 **데이터 원본** 창을 **WPF 디자이너**합니다.  
  
- 만들기는 <xref:System.Windows.Controls.DataGrid> 각각에 대 한 관련된 세부 정보를 표시 하는 컨트롤 순서를 선택 합니다. 자식 엔터티를 끌어 컨트롤을 만든 합니다 **데이터 원본** 창에서 창 **WPF 디자이너**합니다.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>전제 조건  
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- AdventureWorksLT 샘플 데이터베이스가 연결된 SQL Server 또는 SQL Server Express의 실행 중인 인스턴스 액세스 권한. AdventureWorksLT 데이터베이스를 다운로드할 수 있습니다 합니다 [CodePlex 웹 사이트](http://go.microsoft.com/fwlink/?linkid=87843)합니다.  
  
  또한 다음 개념에 대한 지식은 연습을 완료하는 데 반드시 필요하지는 않지만 사전에 파악해 두면 유용할 수 있습니다.  
  
- 엔터티 데이터 모델 및 ADO.NET Entity Framework 자세한 내용은 [Entity Framework 개요](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)합니다.  
  
- WPF 디자이너 사용법. 자세한 내용은 [WPF 및 Silverlight 디자이너 개요](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)합니다.  
  
- WPF 데이터 바인딩. 자세한 내용은 [데이터 바인딩 개요](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)를 참조하세요.  
  
## <a name="creating-the-project"></a>프로젝트 만들기  
 주문 레코드를 표시 하려면 새 WPF 프로젝트를 만듭니다.  
  
#### <a name="to-create-a-new-wpf-project"></a>새 WPF 프로젝트를 만들려면  
  
1. Visual Studio를 시작합니다.  
  
2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.  
  
3. 확장 **Visual C#** 하거나 **Visual Basic**를 선택한 후 **Windows**합니다.  
  
4. 했는지 **.NET Framework 4** 대화 상자의 맨 위에 있는 콤보 상자에서를 선택 합니다. <xref:System.Windows.Controls.DataGrid> 이 연습에서 사용 하는 컨트롤은.NET Framework 4 에서만 사용할 수 있습니다.  
  
5. **WPF 애플리케이션** 프로젝트 템플릿을 선택합니다.  
  
6. **이름** 상자에 `AdventureWorksOrdersViewer`을 입력합니다.  
  
7. **확인**을 클릭합니다.  
  
     Visual Studio 만듭니다는 `AdventureWorksOrdersViewer` 프로젝트입니다.  
  
## <a name="creating-an-entity-data-model-for-the-application"></a>응용 프로그램에 대 한 엔터티 데이터 모델 만들기  
 데이터 바인딩된 컨트롤을 만들려면 먼저 애플리케이션의 데이터 모델을 정의하고 **데이터 원본** 창에 추가해야 합니다. 이 연습에서는 데이터 모델은 엔터티 데이터 모델.  
  
#### <a name="to-create-an-entity-data-model"></a>엔터티 데이터 모델을 만들려면  
  
1. 에 **데이터** 메뉴에서 클릭 **새 데이터 소스 추가** 여는 **데이터 소스 구성 마법사**합니다.  
  
2. 에 **데이터 소스 형식 선택** 페이지에서 클릭 **데이터베이스**를 클릭 하 고 **다음**합니다.  
  
3. 에 **데이터베이스 모델 선택** 페이지에서 **엔터티 데이터 모델**를 클릭 하 고 **다음**합니다.  
  
4. 에 **Model 콘텐츠 선택** 페이지에서 클릭 **데이터베이스에서 생성**를 클릭 하 고 **다음**합니다.  
  
5. 에 **데이터 연결 선택** 페이지에서 다음 중 하나를 수행 합니다.  
  
   - AdventureWorksLT 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.  
  
      또는  
  
   - 클릭 **새 연결** AdventureWorksLT 데이터베이스에 대 한 연결을 만듭니다.  
  
     있는지 확인 합니다 **으로 App.Config의 entity 연결 설정 저장** 옵션을 선택한 다음 클릭 **다음**합니다.  
  
6. 에 **데이터베이스 개체 선택** 페이지에서 **테이블**, 다음 테이블을 선택 하 고:  
  
   - **SalesOrderDetail**  
  
   - **SalesOrderHeader**  
  
7. **마침**을 클릭합니다.  
  
8. 프로젝트를 빌드합니다.  
  
## <a name="creating-data-bound-controls-that-display-the-orders"></a>주문을 표시 하는 컨트롤 데이터 바인딩 만들기  
 끌어 주문 레코드를 표시 하는 컨트롤을 만들 합니다 `SalesOrderHeaders` 에서 엔터티는 **데이터 원본** 창에서 WPF 디자이너로 합니다.  
  
#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>주문 레코드를 표시 하는 데이터 바인딩된 컨트롤을 만들려면  
  
1. **솔루션 탐색기**에서 MainWindow.xaml을 두 번 클릭 합니다.  
  
    WPF 디자이너에서 창이 열립니다.  
  
2. XAML 편집 때문 **높이** 하 고 **너비** 속성 800으로 설정 됩니다  
  
3. 에 **데이터 원본** 창 드롭다운 메뉴를 클릭 합니다 **SalesOrderHeaders** 노드를 선택 **세부 정보**합니다.  
  
4. **SalesOrderHeaders** 노드를 확장합니다.  
  
5. 그런 다음 드롭다운 메뉴를 클릭 **SalesOrderID** 선택한 **ComboBox**합니다.  
  
6. 다음 자식 노드 각각에 대 한 합니다 **SalesOrderHeaders** 노드를 노드 드롭 다운 메뉴를 다음 클릭 하 고 선택 **None**:  
  
   - **RevisionNumber**  
  
   - **OnlineOrderFlag**  
  
   - **ShipToAddressID**  
  
   - **BillToAddressID**  
  
   - **CreditCardApprovalCode**  
  
   - **SubTotal**  
  
   - **TaxAmt**  
  
   - **Freight**  
  
   - **rowguid**  
  
   - **ModifiedDate**  
  
     이 작업을 수행하면 다음 단계에서 이러한 노드에 대해 데이터 바인딩된 컨트롤이 작성되지 않습니다. 이 연습에서는 최종 사용자가 이 데이터를 확인하지 않아도 된다고 가정합니다.  
  
7. **데이터 원본** 창으로 끕니다 합니다 **SalesOrderHeaders** 의 창에 노드 **WPF 디자이너**합니다.  
  
    Visual Studio의 데이터에 바인딩되는 컨트롤 집합을 만드는 XAML을 생성 합니다 **SalesOrderHeaders** 엔터티 및 데이터를 로드 하는 코드입니다. 생성 된 XAML 및 코드에 대 한 자세한 내용은 참조 하세요. [Visual Studio에서 데이터를 바인딩할 WPF 컨트롤](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)합니다.  
  
8. 디자이너에서 콤보 상자를 다음를 클릭 합니다 **판매 주문 ID** 레이블.  
  
9. **속성** 창에서 **IsReadOnly** 속성 옆의 확인란을 선택합니다.  
  
## <a name="creating-a-datagrid-that-displays-the-order-details"></a>주문 세부 정보를 표시 하는 DataGrid를 만들기  
 만들기는 <xref:System.Windows.Controls.DataGrid> 끌어서 주문 세부 정보를 표시 하는 컨트롤을 `SalesOrderDetails` 에서 엔터티를 **데이터 원본** 창에서 WPF 디자이너로 합니다.  
  
#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>주문 세부 정보를 표시 하는 DataGrid를 만들려면  
  
1. 에 **데이터 원본** 창 찾을 합니다 **SalesOrderDetails** 의 자식 노드를 **SalesOrderHeaders** 노드.  
  
   > [!NOTE]
   > 이기도 한 **SalesOrderDetails** 피어 노드는 **SalesOrderHeaders** 노드. 자식 노드를 선택 해야 합니다 **SalesOrderHeaders** 노드.  
  
2. 자식 확장 **SalesOrderDetails** 노드.  
  
3. 다음 자식 노드 각각에 대 한 합니다 **SalesOrderDetails** 노드를 노드 드롭 다운 메뉴를 다음 클릭 하 고 선택 **None**:  
  
   - **SalesOrderID**  
  
   - **SalesOrderDetailID**  
  
   - **rowguid**  
  
   - **ModifiedDate**  
  
     이렇게 하면 Visual Studio에서이 데이터를 비롯 하 여는 <xref:System.Windows.Controls.DataGrid> 다음 단계에서 만든 컨트롤입니다. 이 연습에서는 최종 사용자가 이 데이터를 확인하지 않아도 된다고 가정합니다.  
  
4. **데이터 원본** 창에서 끌어 자식 **SalesOrderDetails** 의 창에 노드 **WPF 디자이너**.  
  
    Visual Studio에서 새 데이터 바인딩된을 정의 하는 XAML 생성 <xref:System.Windows.Controls.DataGrid> 컨트롤과 컨트롤 디자이너에 나타납니다. Visual Studio는 또한 생성 된 업데이트 `GetSalesOrderHeadersQuery` 데이터를 포함 하려면 코드 숨김 파일에서 메서드를 **SalesOrderDetails** 엔터티.  
  
## <a name="testing-the-application"></a>애플리케이션 테스트  
 빌드 및 주문 레코드를 표시 하는지 확인 하려면 응용 프로그램을 실행 합니다.  
  
#### <a name="to-test-the-application"></a>애플리케이션을 테스트하려면  
  
1. **F5**키를 누릅니다.  
  
     애플리케이션이 빌드되고 실행됩니다. 다음 사항을 확인합니다.  
  
    - 합니다 **판매 주문 ID** 콤보 상자에 표시 됩니다 **71774**합니다. 엔터티의 첫 번째 순서 ID입니다.  
  
    - 선택 하면 각 주문에 대 한 합니다 **판매 주문 ID** 콤보 상자에 자세한 주문 정보가 표시 됩니다는 <xref:System.Windows.Controls.DataGrid>합니다.  
  
2. 애플리케이션을 닫습니다.  
  
## <a name="next-steps"></a>다음 단계  
 이 연습을 완료 한 후 사용 하는 방법에 알아봅니다.는 **데이터 원본** WPF 바인딩할 Visual Studio의 창 다른 형식의 데이터 소스를 제어 합니다. 자세한 내용은 [WCF 데이터 서비스에 WPF 바인딩 컨트롤](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) 하 고 [WPF 바인딩 컨트롤을 데이터 집합을](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [WPF 응용 프로그램에서 관련 데이터 표시](../data-tools/display-related-data-in-wpf-applications.md)