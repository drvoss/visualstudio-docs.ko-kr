---
title: Bind WPF controls to a WCF data service | Microsoft Docs
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
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a3d1aab68e3dc9f33e0b3e9f9a5665d59f6f2ddc
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299412"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>WCF 데이터 서비스에 WPF 컨트롤 바인딩
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 데이터 바인딩된 컨트롤을 포함하는 WPF 애플리케이션을 만듭니다. 이러한 컨트롤은 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]에서 캡슐화된 고객 레코드에 바인딩됩니다. 또한 고객이 레코드를 보고 업데이트하는 데 사용할 수 있는 단추도 추가합니다.

 이 연습에서는 다음 작업을 수행합니다.

- AdventureWorksLT 샘플 데이터베이스의 데이터에서 생성되는 엔터티 데이터 모델을 만듭니다.

- Creating a [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] that exposes the data in the Entity Data Model to a WPF application.

- **데이터 원본** 창에서 WPF 디자이너로 항목을 끌어 데이터 바인딩된 컨트롤 집합을 만듭니다.

- 고객 레코드를 앞뒤로 탐색하는 데 사용할 단추를 만듭니다.

- Creating a button that saves changes to data in the controls to the [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] and the underlying data source.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Prerequisites
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- AdventureWorksLT 샘플 데이터베이스가 연결된 SQL Server 또는 SQL Server Express의 실행 중인 인스턴스 액세스 권한. You can download the AdventureWorksLT database from the [CodePlex Web site](https://go.microsoft.com/fwlink/?linkid=87843).

  또한 다음 개념에 대한 지식은 연습을 완료하는 데 반드시 필요하지는 않지만 사전에 파악해 두면 유용할 수 있습니다.

- WCF Data Services. For more information, see [Overview](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).

- [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)]의 데이터 모델

- 엔터티 데이터 모델 및 ADO.NET Entity Framework For more information, see [Entity Framework Overview](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- WPF 디자이너 사용법. For more information, see [WPF and Silverlight Designer Overview](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- WPF 데이터 바인딩. 자세한 내용은 [데이터 바인딩 개요](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)를 참조하세요.

## <a name="create-the-service-project"></a>Create the service project
 이 연습에서는 먼저 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]용 프로젝트를 만듭니다.

#### <a name="to-create-the-service-project"></a>해당 서비스 프로젝트를 만들려면

1. Visual Studio를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

3. **Visual C#** 또는 **Visual Basic**을 확장한 다음, **웹**을 선택합니다.

4. **ASP.NET 웹 애플리케이션** 프로젝트 템플릿을 선택합니다.

5. In the **Name** box, type `AdventureWorksService` and click **OK**.

     Visual Studio creates the `AdventureWorksService` project.

6. **솔루션 탐색기**에서 **Default.aspx**를 오른쪽 마우스 단추로 클릭하고 **삭제**를 선택합니다. 이 연습에서는 해당 파일이 필요하지 않습니다.

## <a name="create-an-entity-data-model-for-the-service"></a>Create an Entity Data Model for the service
 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]를 사용하여 애플리케이션에 데이터를 표시하려면 서비스에 대해 데이터 모델을 정의해야 합니다. The [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] supports two types of data models: Entity Data Models, and custom data models that are defined by using common language runtime (CLR) objects that implement the <xref:System.Linq.IQueryable%601> interface. 이 연습에서는 데이터 모델에 대해 엔터티 데이터 모델을 만듭니다.

#### <a name="to-create-an-entity-data-model"></a>엔터티 데이터 모델을 만들려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

2. 설치된 템플릿 목록에서 **데이터**를 클릭한 다음, **ADO.NET 엔터티 데이터 모델** 프로젝트 항목을 선택합니다.

3. Change the name to `AdventureWorksModel.edmx`, and click **Add**.

     **엔터티 데이터 모델** 마법사가 열립니다.

4. **모델 콘텐츠 선택** 페이지에서 **데이터베이스에서 생성**을 클릭한 후, **다음**을 클릭합니다.

5. **데이터 연결 선택** 페이지에서 다음 옵션 중 하나를 선택합니다.

    - AdventureWorksLT 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

    - **새 연결**을 클릭하고 AdventureWorksLT 데이터베이스에 대한 연결을 만듭니다.

6. **데이터 연결 선택** 페이지에서 **다른 이름으로 App.Config의 엔터티 연결 설정 저장** 옵션이 선택되어 있는지 확인한 후, **다음**을 클릭합니다.

7. **데이터베이스 개체 선택** 페이지에서 **테이블**을 확장한 다음, **SalesOrderHeader** 테이블을 선택합니다.

8. **마침**을 클릭합니다.

## <a name="create-the-service"></a>서비스 만들기
 Create a [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] to expose the data in the Entity Data Model to a WPF application.

#### <a name="to-create-the-service"></a>해당 서비스를 만들려면

1. **프로젝트** 메뉴에서 **새 항목 추가**를 선택합니다.

2. In the Installed Templates list, click **Web**, and then select the **WCF Data Service** project item.

3. In the **Name** box, type `AdventureWorksService.svc`, and click **Add**.

     Visual Studio adds the `AdventureWorksService.svc` to the project.

## <a name="configure-the-service"></a>서비스 구성
 작성한 엔터티 데이터 모델에 대해 작동하도록 서비스를 구성해야 합니다.

#### <a name="to-configure-the-service"></a>서비스를 구성하려면

1. In the `AdventureWorks.svc` code file, replace the `AdventureWorksService` class declaration with the following code.

     [!code-csharp[Data_WPFWCF#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs#1)]
     [!code-vb[Data_WPFWCF#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb#1)]

     This code updates the `AdventureWorksService` class, so that it derives from a <xref:System.Data.Services.DataService%601> that operates on the `AdventureWorksLTEntities` object context class in your Entity Data Model. 또한 서비스의 클라이언트에 `InitializeService` 엔터티에 대한 모든 읽기/쓰기 권한을 허용하도록 `SalesOrderHeader` 메서드를 업데이트합니다.

2. 프로젝트를 빌드하고 오류가 없이 빌드되는지 확인합니다.

## <a name="create-the-wpf-client-application"></a>Create the WPF client application
 [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]에서 데이터를 표시하려면 서비스를 기반으로 하는 데이터 소스를 사용하여 새 WPF 애플리케이션을 만듭니다. 이 연습 뒷부분에서 애플리케이션에 데이터 바인딩된 컨트롤을 추가합니다.

#### <a name="to-create-the-wpf-client-application"></a>WPF 클라이언트 애플리케이션을 만들려면

1. **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭하고, **추가**를 클릭하고, **새 프로젝트**를 선택합니다.

2. **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음, **Windows**를 선택합니다.

3. **WPF 애플리케이션** 프로젝트 템플릿을 선택합니다.

4. **이름** 상자에 `AdventureWorksSalesEditor`를 입력하고 **확인**을 클릭합니다.

     Visual Studio adds the `AdventureWorksSalesEditor` project to the solution.

5. **데이터** 메뉴에서 **데이터 소스 표시**를 클릭합니다.

     **데이터 원본** 창이 열립니다.

6. **데이터 소스** 창에서 **새 데이터 소스 추가**를 클릭합니다.

     **데이터 원본 구성** 마법사가 열립니다.

7. 마법사의 **데이터 원본 형식 선택** 페이지에서 **서비스**를 선택한 후, **다음**을 클릭합니다.

8. **서비스 참조 추가** 대화 상자에서 **검색**을 클릭합니다.

     Visual Studio searches the current solution for available services, and adds `AdventureWorksService.svc` to the list of available services in the **Services** box.

9. In the **Namespace** box, type `AdventureWorksService`.

10. **서비스** 상자에서 **AdventureWorksService.svc**를 클릭한 다음, **확인**을 클릭합니다.

     Visual Studio downloads the service information, and then returns to the **Data Source Configuration** wizard.

11. **서비스 참조 추가** 페이지에서 **마침**을 클릭합니다.

     Visual Studio는 서비스에서 반환하는 데이터를 나타내는 노드를 **데이터 원본** 창에 추가합니다.

## <a name="define-the-user-interface-of-the-window"></a>Define the user interface of the window
 WPF 디자이너에서 XAML을 수정하여 창에 여러 단추를 추가합니다. 이 연습 뒷부분에서 사용자가 이러한 단추를 사용해 판매 레코드를 보고 업데이트할 수 있도록 하는 코드를 추가합니다.

#### <a name="to-create-the-window-layout"></a>창 레이아웃을 만들려면

1. In **Solution Explorer**, double-click MainWindow.xaml.

     WPF 디자이너에서 창이 열립니다.

2. 디자이너의 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 뷰에서 `<Grid>` 태그 사이에 다음 코드를 추가합니다.

    ```
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="525" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3. 프로젝트를 빌드합니다.

## <a name="create-the-data-bound-controls"></a>Create the data-bound controls
 Create controls that display customer records by dragging the `SalesOrderHeaders` node from the **Data Sources** window to the designer.

#### <a name="to-create-the-data-bound-controls"></a>데이터 바인딩된 컨트롤을 만들려면

1. **데이터 원본** 창에서 **SalesOrderHeaders** 노드의 드롭다운 메뉴를 클릭하고 **정보**를 선택합니다.

2. **SalesOrderHeaders** 노드를 확장합니다.

3. 이 예에서는 일부 필드를 표시하지 않을 것이므로 다음 노드 옆의 드롭다운 메뉴를 클릭하고 **없음**을 선택합니다.

   - **CreditCardApprovalCode**

   - **ModifiedDate**

   - **OnlineOrderFlag**

   - **RevisionNumber**

   - **Rowguid**

     이 작업을 수행하면 다음 단계에서 이러한 노드에 대해 데이터 바인딩된 컨트롤이 작성되지 않습니다. For this walkthrough, assume that the end user does not need to see this data.

4. **데이터 원본** 창에서 단추가 포함된 행 아래의 데이터 그리드 행으로 **SalesOrderHeaders** 노드를 끌어 옵니다.

    Visual Studio는 **Product** 테이블의 데이터에 바인딩되는 컨트롤 집합을 만드는 XAML 및 코드를 생성합니다. For more information about the generated XAML and code, see [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

5. 디자이너에서 **고객 ID** 레이블 옆의 텍스트 상자를 클릭합니다.

6. **속성** 창에서 **IsReadOnly** 속성 옆의 확인란을 선택합니다.

7. 다음의 각 텍스트 상자에 대해 **IsReadOnly** 속성을 설정합니다.

   - **구매 주문 번호**

   - **판매 주문 ID**

   - **판매 주문 번호**

## <a name="load-the-data-from-the-service"></a>서비스에서 데이터 로드
 Use the service proxy object to load sales data from the service. Then assign the returned data to the data source for the <xref:System.Windows.Data.CollectionViewSource> in the WPF window.

#### <a name="to-load-the-data-from-the-service"></a>서비스에서 데이터를 로드하려면

1. 디자이너를 만들려면를 `Window_Loaded` 이벤트 처리기에서 텍스트를 두 번 클릭: **MainWindow**.

2. 이벤트 처리기를 다음 코드로 바꿉니다. 이 코드의 *localhost*주소는 사용 중인 개발 컴퓨터의 로컬 호스트 주소로 바꿔야 합니다.

     [!code-csharp[Data_WPFWCF#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFWCF#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#2)]

## <a name="navigatesales-records"></a>Navigatesales records
 사용자가 **\<** 및 **>** 단추를 사용하여 판매 레코드를 스크롤할 수 있도록 하는 코드를 추가합니다.

#### <a name="to-enable-users-to-navigate-sales-records"></a>사용자가 판매 레코드를 탐색할 수 있도록 설정하려면

1. 디자이너의 창 화면에서 **<** 단추를 두 번 클릭합니다.

     Visual Studio가 코드 숨김 파일을 열고 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 이벤트에 대해 새 `backButton_Click` 이벤트 처리기를 만듭니다.

2. 다음 코드를 생성된 `backButton_Click` 이벤트 처리기에 추가합니다.

     [!code-csharp[Data_WPFWCF#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFWCF#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#3)]

3. 디자이너로 돌아와서 **>** 단추를 두 번 클릭합니다.

     Visual Studio가 코드 숨김 파일을 열고 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 이벤트에 대해 새 `nextButton_Click` 이벤트 처리기를 만듭니다.

4. 다음 코드를 생성된 `nextButton_Click` 이벤트 처리기에 추가합니다.

     [!code-csharp[Data_WPFWCF#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFWCF#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#4)]

## <a name="saving-changes-to-sales-records"></a>Saving changes to sales records
 Add code that enables users to both view and save changes to sales records by using the **Save changes** button.

#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>판매 레코드 변경 내용을 저장하는 기능을 추가하려면

1. 디자이너에서 **변경 내용 저장** 단추를 두 번 클릭합니다.

     Visual Studio가 코드 숨김 파일을 열고 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 이벤트에 대해 새 `saveButton_Click` 이벤트 처리기를 만듭니다.

2. 다음 코드를 `saveButton_Click` 이벤트 처리기에 추가합니다.

     [!code-csharp[Data_WPFWCF#5](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#5)]
     [!code-vb[Data_WPFWCF#5](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#5)]

## <a name="testing-the-application"></a>애플리케이션 테스트
 애플리케이션을 빌드하고 실행하여 고객 레코드를 보고 업데이트할 수 있는지 확인합니다.

#### <a name="to-test-the-application"></a>애플리케이션을 테스트하려면

1. On **Build** menu, click **Build Solution**. 솔루션이 오류 없이 빌드되는지 확인합니다.

2. Press **Ctrl+F5**.

     Visual Studio는 디버깅하지 않고 **AdventureWorksService** 프로젝트를 시작합니다.

3. **솔루션 탐색기**에서 **AdventureWorksSalesEditor** 프로젝트를 마우스 오른쪽 단추로 클릭합니다.

4. 컨텍스트 메뉴의 **디버그**에서 **새 인스턴스 시작**을 클릭합니다.

     애플리케이션이 실행됩니다. 다음 사항을 확인합니다.

    - 판매 주문 ID가 **71774**인 첫 번째 판매 레코드의 서로 다른 데이터 필드가 텍스트 상자에 표시됩니다.

    - **>** 또는 **<** 단추를 클릭하여 다른 판매 레코드를 탐색할 수 있습니다.

5. 판매 레코드 중 하나의 **주석** 상자에 텍스트를 입력한 다음, **변경내용 저장**을 클릭합니다.

6. 애플리케이션을 닫았다가 Visual Studio에서 다시 시작합니다.

7. 변경한 판매 레코드로 이동하여 애플리케이션을 닫았다가 다시 열어도 변경 내용이 그대로 유지되는지 확인합니다.

8. 애플리케이션을 닫습니다.

## <a name="next-steps"></a>다음 단계
 이 연습을 완료하고 나면 다음과 같은 관련 작업을 수행할 수 있습니다.

- Visual Studio의 **데이터 원본** 창을 사용하여 WPF 컨트롤을 다른 형식의 데이터 원본에 바인딩하는 방법을 알아봅니다. For more information, see [Bind WPF controls to a dataset](../data-tools/bind-wpf-controls-to-a-dataset.md).

- Visual Studio의 **데이터 원본** 창을 사용하여 WPF 컨트롤에 관련 데이터(즉, 부모-자식 관계가 있는 데이터)를 표시하는 방법을 알아봅니다. For more information, see [Walkthrough: Displaying Related Data in a WPF Application](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).

## <a name="see-also"></a>관련 항목:
 [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [Bind WPF controls to data in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [Bind WPF controls to a dataset](../data-tools/bind-wpf-controls-to-a-dataset.md) [Overview](https://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb) [Entity Framework Overview](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0) [WPF and Silverlight Designer Overview](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62) [Data Binding Overview](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
