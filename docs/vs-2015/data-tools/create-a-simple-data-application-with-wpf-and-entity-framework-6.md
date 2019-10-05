---
title: WPF 및 Entity Framework 6을 사용 하 여 간단한 데이터 응용 프로그램 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 65929fab-5d78-4e04-af1e-cf4957f230f6
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: decb17be7caa4ea0a300ddb4378ac0ad11520109
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145867"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF 및 Entity Framework 6을 사용하여 간단한 데이터 애플리케이션 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에는 SQL Server LocalDB, Northwind 데이터베이스, Entity Framework 6 및 Windows Presentation Foundation을 사용 하 여 Visual Studio에서 기본 "데이터 폼" 응용 프로그램을 만드는 방법을 보여 줍니다. 마스터-세부 뷰를 사용 하 여 기본 데이터 바인딩 작업을 수행 하는 방법을 보여 줍니다과 함께 사용자 지정 "바인딩 탐색기" "다음으로 이동" 단추를 사용 하 여 "이전으로 이동," "처음 이동" 이동 "을 종료 하려면"에 "업데이트" 및 "삭제"입니다.  
  
 이 문서에서는 Visual Studio에서 데이터 도구를 사용 하 여에 중점을 둡니다 및 모든 수준에서 기본 기술에 설명 하려고 하지 않습니다. XAML, Entity Framework 및 SQL에 대 한 기본 지식이 있다고 가정 합니다. 또한이 예제에서는 WPF 응용 프로그램에 대 한 표준 MVVM 아키텍처를 보여 주지 않습니다. 그러나 몇 가지 수정 사항이 MVVM 응용 프로그램 자체에이 코드를 복사할 수 있습니다.  
  
## <a name="install-and-connect-to-northwind"></a>설치 하 고 Northwind로 연결  
 이 예제에서는 Northwind 샘플 데이터베이스 및 SQL Server Express LocalDB를 사용 합니다. 에뮬레이터가 작동 됩니다 다른 SQL 데이터베이스 제품과 마찬가지로 해당 제품에 ADO.NET 데이터 공급자는 Entity Framework를 지 원하는 경우.  
  
1. 아직 SQL Server 2014 LocalDB Express 32 비트에서 설치 합니다 [SQL Server 버전 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express)합니다.  
  
2. 다음 지침에 따라 Northwind 샘플 데이터베이스를 설치 합니다. [SQL Server 예제 데이터베이스 설치](../data-tools/install-sql-server-sample-databases.md)합니다.  
  
3. [새 연결 추가](../data-tools/add-new-connections.md) Northwind에 대 한 합니다.  
  
## <a name="configure-the-project"></a>프로젝트 구성  
  
1. Visual Studio에서 선택 **파일 &#124; 새 프로젝트** 한 다음 새 C# WPF 응용 프로그램을 만듭니다.  
  
2. 다음 Entity Framework 6에 대 한 NuGet 패키지를 추가 합니다. 솔루션 탐색기에서 프로젝트 노드를 선택 합니다. 주 메뉴에서 선택 **프로젝트 &#124; NuGet 패키지 관리...**  
  
     ![메뉴 항목 NuGet 패키지 관리](../data-tools/media/raddata-vs2015-manage-nuget-packages.png "raddata_vs2015_manage_nuget_packages")  
  
3. NuGet 패키지 관리자를 클릭 합니다 **찾아보기** 링크 합니다. Entity Framework 목록의 최상위 패키지 때문일 수 있습니다. 클릭 **설치** 오른쪽 창에서를 따릅니다. 출력 창에서는 설치가 완료 되 면 알려줍니다를 보여 줍니다.  
  
     ![Entity Framework NuGet 패키지](../data-tools/media/raddata-vs2015-nuget-ef.png "raddata_vs2015_Nuget_EF")  
  
4. 이제 Northwind 데이터베이스를 기반으로 모델을 만들려면 Visual Studio를 사용할 수 있습니다.  
  
## <a name="create-the-model"></a>모델 만들기  
  
1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 선택 **추가 &#124; 새 항목**합니다. C# 노드를 아래 왼쪽된 창에서 선택 **데이터** 가운데 창에서 선택 하 고 **ADO.NET Entity Data Model**합니다.  
  
    ![Entity Framework 모델 새 프로젝트 항목](../data-tools/media/raddata-ef-new-project-item.png "raddata EF 새 프로젝트 항목")  
  
2. 모델을 호출 `Northwind_model` 고 확인을 선택 합니다. 그러면 합니다 **엔터티 데이터 모델 마법사**합니다. 선택할 **데이터베이스의 EF 디자이너** 을 클릭 한 다음 **다음**합니다.  
  
    ![데이터베이스에서 EF 모델](../data-tools/media/raddata-ef-model-from-database.png "raddata 데이터베이스에서 EF 모델")  
  
3. 다음 화면에서 LocalDB Northwind에 연결 하 고 선택 **다음**합니다.  
  
4. 마법사의 다음 페이지에서 테이블, 저장된 프로시저 및 다른 데이터베이스에에서 포함할 개체를 Entity Framework 모델을 선택 합니다. 트리 뷰에서 dbo 노드를 확장 하 고 고객, 주문 및 주문 세부 정보를 선택 합니다. 기본값이 선택 된 상태로 두고 클릭 **완료**합니다.  
  
    ![모델에 대 한 데이터베이스 개체 선택](../data-tools/media/raddata-choose-ef-objects.png "raddata EF 개체 선택")  
  
5. 마법사는 Entity Framework 모델을 나타내는 C# 클래스를 생성 합니다. 이전 일반 C# 클래스 이며는 것은 WPF 사용자 인터페이스에 데이터 바인딩합니다. .Edmx 파일에는 관계 및 데이터베이스의 개체를 사용 하 여 클래스를 연결 하는 다른 메타 데이터 설명 합니다.  .Tt 파일은 모델에서 동작 하 고 데이터베이스에 변경 내용을 저장 하는 코드 생성을 T4 템플릿입니다. Northwind_model 노드 아래의 솔루션 탐색기에서 이러한 모든 파일을 확인할 수 있습니다.  
  
    ![솔루션 탐색기 EF 모델 파일](../data-tools/media/raddata-solution-explorer-ef-model-files.png "raddata 솔루션 탐색기 EF 모델 파일")  
  
    .Edmx 파일에 대 한 디자이너 화면을 사용 하면 일부 속성 및 모델의 관계를 수정할 수 있습니다. 디자이너를 사용 하 여이 연습을 하지 않습니다.  
  
6. .Tt 파일은 범용 및 ObservableCollections 하며 WPF 데이터 바인딩 작업 중 하나를 조정 해야 합니다.  솔루션 탐색기에서 Northwind_model.tt 찾을 때까지 Northwind_model 노드를 확장 합니다. (있는지 **하지** 에 *입니다. 상황에 맞는.tt 파일은.edmx 파일의 바로 아래).  
  
   - 두 바꿀 <xref:System.Collections.ICollection> 사용 하 여 <xref:System.Collections.ObjectModel.ObservableCollection%601>입니다.  
  
   - 첫 번째 항목을 바꾸려면 <xref:System.Collections.Generic.HashSet%601> 사용 하 여 <xref:System.Collections.ObjectModel.ObservableCollection%601> 51 줄. HashSet의 두 번째 발생을 대체 하지 않습니다  
  
   - 유일한 대체할 <xref:System.Collections.Generic> (줄 근처 334) 사용 하 여 <xref:System.Collections.ObjectModel>입니다.  
  
7. 키를 눌러 **Ctrl + Shift + B** 프로젝트를 빌드합니다. 빌드가 완료 되 면 모델 클래스는 데이터 원본 마법사에 표시 합니다.  
  
   이제 XAML 페이지에이 모델에서는 보고 탐색 하 고 데이터를 수정할 수 있도록 연결 준비가 되었습니다.  
  
## <a name="databind-the-model-to-the-xaml-page"></a>Databind XAML 페이지 모델  
 사용자 고유의 데이터 바인딩 코드를 작성할 수 있지만 Visual Studio 작업을 수행할 수 있도록 훨씬 쉽습니다.  
  
1. 주 메뉴에서 선택 **프로젝트 &#124; 새 데이터 원본 추가** 불러오려면 합니다 **데이터 소스 구성 마법사**합니다. 선택할 **개체** 바인딩하므로 모델 클래스, 데이터베이스에 없습니다.  
  
     ![개체 소스를 사용 하 여 데이터 소스 구성 마법사](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png "raddata 개체 소스를 사용 하 여 데이터 소스 구성 마법사")  
  
2. 고객을 선택 합니다.  (주문에 대 한 소스 자동으로 생성 됩니다 고객의 주문 탐색 속성에서.)  
  
     ![데이터 원본으로 엔터티 클래스를 추가](../data-tools/media/raddata-add-entity-classes-as-data-sources.png "raddata 엔터티 추가 데이터 원본으로 클래스")  
  
3. 클릭 **마침**  
  
4. 코드 보기에서 MainWindow.xaml을 이동 합니다. 이 예제의 목적에 대 한 매우 간단한는 XAML을 유지 하려고 합니다. 좀 더 구체적인 MainWindow의 제목을 변경 하 고 지금은 600 x 800로 해당 높이 너비를 늘립니다. 항상 변경할 수 있습니다 하 나중입니다. 이제 이러한 세 가지 행 정의 주 표의 고객의 주문을 보여 주는 눈금에 대 한 고객의 세부 정보에 대 한 탐색 단추를 한 개의 행을 추가 합니다.  
  
    ```xaml  
    <Grid.RowDefinitions>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="auto"/>  
               <RowDefinition Height="*"/>  
           </Grid.RowDefinitions>  
    ```  
  
5. 이제 디자이너에서 보기는 있도록 MainWindow.xaml을 엽니다. 이렇게 하면 데이터 소스 창에 도구 상자 옆에 있는 Visual Studio 창 여백에 옵션으로 표시 합니다. 창을 열거나 다른 키를 눌러 탭을 클릭 **Shift + Alt + D** 선택 하거나 **보기 &#124; 다른 Windows &#124; 데이터 원본**. 고객은 클래스 자체의 개별 텍스트 상자에서 각 속성을 표시 하려고 합니다. 먼저 고객 콤보 상자에서 화살표를 클릭 하 고 선택 **세부 정보**합니다. 그런 다음 디자이너 가운데 행에서 이동 하려는 알 수 있도록 디자인 화면의 가운데 부분에 노드를 끕니다.  이 잃어 버리면 하는 경우에 XAML에서 나중에 수동으로 행을 지정할 수 있습니다. 기본적으로 세로 그리드 요소에 배치 된 하지만 시점에서 정렬할 수 폼에서 원하는 합니다.  예를 들어 주소 위에서 위쪽에 이름 텍스트 상자를 배치 하는 것이 해야 합니다. 이 문서에 대 한 샘플 응용 프로그램 필드 다시 정렬 하 고 이러한 두 개의 열으로 다시 정렬.  
  
     ![개별 컨트롤에 고객 데이터 원본 바인딩을](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png "을 개별 컨트롤로 raddata 고객은 데이터 소스 바인딩")  
  
     코드 보기에서 이제 볼 수 있습니다 새 `Grid` 행의 요소 1 (중간 행)의 부모 표입니다. 표에 부모를 `DataContext` 에 추가 된 있는 collectionviewsource에 바인딩하면 참조 특성을 `Windows.Resources` 요소입니다. 예를 들어, 첫 번째 텍스트 상자 때에 해당 데이터 컨텍스트를 지정 된 이름이 "Address"에 바인딩합니다에 매핑되는 `Address` 현재에서 속성 `Customer` CollectionViewSource에는 개체입니다.  
  
    ```xaml  
    <Grid DataContext="{StaticResource customerViewSource}">  
    ```  
  
6. 고객 창의 위쪽에 표시 되 면 아래에 있는 고객의 주문을 반 참조 하려고 합니다. 단일 표 뷰 컨트롤의 순서를 살펴보겠습니다. 예상 대로 작동 하는 마스터-세부 데이터 바인딩, 별도 Orders 노드 필요가 고객 클래스에 Orders 속성에 바인딩하는 것이 중요 한 것입니다. 다음 그림과 같이 주의! 디자이너 2 행에 저장 되도록 폼의 아래쪽 절반을 고객에 게 클래스의 Orders 속성으로를 끕니다.  
  
     ![주문 클래스 그리드로 끌어](../data-tools/media/raddata-drag-orders-classes-as-grid.png "그리드로 끌어 Orders raddata 클래스")  
  
7. Visual Studio UI 컨트롤 모델에서 이벤트에 연결 하는 모든 바인딩 코드를 생성 했습니다. 일부 데이터를 확인 하기 위해 수행 해야 하는 모든 모델을 채우는 코드를 작성 하는 것입니다. 첫 번째 보겠습니다 MainWindow.xaml.cs를 이동 하 고 데이터 컨텍스트에 대해 MainWindow 클래스 데이터 멤버를 추가 합니다. 이 개체에 생성 된 변경 내용 및 모델에서 이벤트를 추적 하는 컨트롤 같이 작동 합니다. 우리는 여기 하는 동안 사용 하 여 나중에 새 고객 또는 새 주문을 추가 하는 두 명의 멤버 추가 하겠습니다. 생성자 초기화 논리를 추가 합니다. 클래스의 맨 위에 다음과 같이 표시 됩니다.  
  
    ```csharp  
    public partial class MainWindow : Window  
       {  
           public Customer newCustomer { get; set; }  
           public Order newOrder { get; set; }  
  
           NorthwindEntities context = new NorthwindEntities();  
           CollectionViewSource custViewSource;  
           CollectionViewSource ordViewSource;  
  
           public MainWindow()  
           {  
               InitializeComponent();  
               newCustomer = new Customer();  
               newOrder = new Order();  
               custViewSource = ((CollectionViewSource)  
                   (FindResource("customerViewSource")));  
               ordViewSource = ((CollectionViewSource)  
                   (FindResource("customerOrdersViewSource")));  
               DataContext = this;  
           }  
    ```  
  
     추가 된 `using` System.Data.Entity Load 확장 메서드를 범위로 가져올에 대 한 지시문:  
  
    ```csharp  
    using System.Data.Entity;  
    ```  
  
     이제 아래로 스크롤하고 Window_Loaded 이벤트 처리기를 찾습니다. Visual Studio에 추가 CollectionViewSource 개체를 확인 합니다. 이 모델을 만들었을 때 선택한 NorthwindEntities 개체를 나타냅니다. 코드를 추가 하겠습니다 Window_loaded 전체 메서드는 이제 다음과 같이 표시 되도록 합니다.  
  
    ```csharp  
    private void Window_Loaded(object sender, RoutedEventArgs e)  
        {  
            // Load is an extension method on IQueryable,    
            // defined in the System.Data.Entity namespace.   
            // This method enumerates the results of the query,    
            // similar to ToList but without creating a list.   
            // When used with Linq to Entities this method    
            // creates entity objects and adds them to the context.   
            context.Customers.Load();  
  
            // After the data is loaded call the DbSet<T>.Local property    
            // to use the DbSet<T> as a binding source.   
            custViewSource.Source = context.Customers.Local;  
        }  
    ```  
  
8. **F5**키를 누릅니다. CollectionViewSource에 및 데이터 그리드에서 해당 주문에 검색 된 첫 번째 고객에 대 한 세부 정보가 표시 됩니다. 서식 지정 하겠습니다 픽스업 하는 훌륭한 아닙니다. 만들 다른 레코드를 보는 방법 및 기본 CRUD 작업을 수행 합니다.  
  
## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>페이지 디자인을 조정 하 고 새로운 고객 및 주문에 대 한 표 추가  
 Visual Studio에서 생성 된 기본 배열을 XAML에서 일부 변경을 수동으로 수행 됩니다 있도록이 응용 프로그램에 대 한 이상적이 지 않습니다. 또한 새 고객 또는 새 주문을 추가 하려면 사용자를 사용 하도록 설정 하려면 몇 가지 "forms" (임, 실제로 표) 해야 합니다.    텍스트 상자에 데이터 바인딩된 없는 별도 집합을 새 customer와 order를 추가할 수 있도록 해야 합니다 `CollectionViewSource`합니다. Visible 속성 처리기 메서드를 설정 하 여 언제 든 지 사용자에 게는 그리드를 제어 됩니다.  
  
 마지막으로, 개별 주문을 삭제 하려면 사용자를 사용 하도록 설정 하려면 주문 표의 각 행에 있는 삭제 단추를 추가 합니다.  
  
 먼저 Windows.Resources에이 스타일을 추가 합니다.  
  
```xaml  
<Style x:Key="Label" TargetType="{x:Type Label}" BasedOn="{x:Null}">  
    <Setter Property="HorizontalAlignment" Value="Left"/>  
    <Setter Property="VerticalAlignment" Value="Center"/>  
    <Setter Property="Margin" Value="3"/>  
    <Setter Property="Height" Value="23"/>  
</Style>  
<Style x:Key="CustTextBox" TargetType="{x:Type TextBox}" BasedOn="{x:Null}">  
    <Setter Property="HorizontalAlignment" Value="Right"/>  
    <Setter Property="VerticalAlignment" Value="Center"/>  
    <Setter Property="Margin" Value="3"/>  
    <Setter Property="Height" Value="26"/>  
    <Setter Property="Width" Value="120"/>  
</Style>  
```  
  
 이 태그를 사용 하 여 전체 외부 표를 다음으로 바꿉니다.  
  
```xaml  
<Grid >  
     <Grid.RowDefinitions>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="auto"/>  
         <RowDefinition Height="*"/>  
     </Grid.RowDefinitions>  
     <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
         <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
         <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
         <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>  
         <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
         <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
         <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
         <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
         <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
         <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
     </StackPanel>  
     <Grid x:Name="existingCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" Margin="5" Visibility="Visible" VerticalAlignment="Top" Background="AntiqueWhite" DataContext="{StaticResource customerViewSource}">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>  
         <TextBox x:Name="customerIDTextBox"  Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
         <TextBox x:Name="cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>  
         <TextBox x:Name="postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <Grid x:Name="newCustomerGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding RelativeSource={RelativeSource FindAncestor, AncestorType={x:Type Window}}, Path=newCustomer, UpdateSourceTrigger=Explicit}" Visibility="Collapsed" Background="CornflowerBlue">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="Customer ID:" Grid.Row="0" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_customerIDTextBox"  Grid.Row="0"  Style="{StaticResource CustTextBox}"   
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Company Name:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_companyNameTextBox"  Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>  
         <Label Content="Contact Name:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Contact Title:"  Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="City:" Grid.Column="1" Grid.Row="0"  Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_cityTextBox" Grid.Column="1" Grid.Row="0" Style="{StaticResource CustTextBox}"   
                  Text="{Binding City, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Country:" Grid.Column="1" Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_countryTextBox" Grid.Column="1" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Country, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Fax:" Grid.Column="1" Grid.Row="2" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_faxTextBox" Grid.Column="1" Grid.Row="2" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Fax, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Phone:" Grid.Column="1" Grid.Row="3" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_phoneTextBox" Grid.Column="1" Grid.Row="3" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Phone, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Postal Code:" Grid.Column="1" Grid.Row="4" VerticalAlignment="Center" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_postalCodeTextBox" Grid.Column="1" Grid.Row="4" Style="{StaticResource CustTextBox}"   
                  Text="{Binding PostalCode, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Region:" Grid.Column="1" Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_regionTextBox" Grid.Column="1" Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Region, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <Grid x:Name="newOrderGrid" Grid.Row="1" HorizontalAlignment="Left" VerticalAlignment="Top" Margin="5" DataContext="{Binding Path=newOrder, Mode=TwoWay}" Visibility="Collapsed" Background="LightGreen">  
         <Grid.ColumnDefinitions>  
             <ColumnDefinition Width="Auto" MinWidth="233"/>  
             <ColumnDefinition Width="Auto" MinWidth="397"/>  
         </Grid.ColumnDefinitions>  
         <Grid.RowDefinitions>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
             <RowDefinition Height="Auto"/>  
         </Grid.RowDefinitions>  
         <Label Content="New Order Form" FontWeight="Bold"/>  
         <Label Content="Employee ID:"  Grid.Row="1" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_employeeIDTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"   
                  Text="{Binding EmployeeID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Order Date:"  Grid.Row="2" Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_orderDatePicker" Grid.Row="2"  HorizontalAlignment="Right" Width="120"  
                 SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Required Date:" Grid.Row="3" Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_requiredDatePicker" Grid.Row="3" HorizontalAlignment="Right" Width="120"  
                  SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Shipped Date:"  Grid.Row="4"  Style="{StaticResource Label}"/>  
         <DatePicker x:Name="add_shippedDatePicker"  Grid.Row="4"  HorizontalAlignment="Right" Width="120"  
                 SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
         <Label Content="Ship Via:"  Grid.Row="5" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_ShipViaTextBox"  Grid.Row="5" Style="{StaticResource CustTextBox}"   
                  Text="{Binding ShipVia, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
         <Label Content="Freight"  Grid.Row="6" Style="{StaticResource Label}"/>  
         <TextBox x:Name="add_freightTextBox" Grid.Row="6" Style="{StaticResource CustTextBox}"   
                  Text="{Binding Freight, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>  
     </Grid>  
     <DataGrid x:Name="ordersDataGrid" SelectionUnit="Cell" SelectionMode="Single" AutoGenerateColumns="False" CanUserAddRows="false" IsEnabled="True" EnableRowVirtualization="True" Width="auto" ItemsSource="{Binding Source={StaticResource customerOrdersViewSource}}" Margin="10,10,10,10" Grid.Row="2" RowDetailsVisibilityMode="VisibleWhenSelected">  
         <DataGrid.Columns>  
             <DataGridTemplateColumn>  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <Button Content="Delete"  Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="customerIDColumn" Binding="{Binding CustomerID}" Header="Customer ID" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="employeeIDColumn" Binding="{Binding EmployeeID}" Header="Employee ID" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="freightColumn" Binding="{Binding Freight}" Header="Freight" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="orderDateColumn" Header="Order Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding OrderDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="orderIDColumn" Binding="{Binding OrderID}" Header="Order ID" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="requiredDateColumn" Header="Required Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding RequiredDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="shipAddressColumn" Binding="{Binding ShipAddress}" Header="Ship Address" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipCityColumn" Binding="{Binding ShipCity}" Header="Ship City" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipCountryColumn" Binding="{Binding ShipCountry}" Header="Ship Country" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipNameColumn" Binding="{Binding ShipName}" Header="Ship Name" Width="SizeToHeader"/>  
             <DataGridTemplateColumn x:Name="shippedDateColumn" Header="Shipped Date" Width="SizeToHeader">  
                 <DataGridTemplateColumn.CellTemplate>  
                     <DataTemplate>  
                         <DatePicker SelectedDate="{Binding ShippedDate, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true, UpdateSourceTrigger=PropertyChanged}"/>  
                     </DataTemplate>  
                 </DataGridTemplateColumn.CellTemplate>  
             </DataGridTemplateColumn>  
             <DataGridTextColumn x:Name="shipPostalCodeColumn" Binding="{Binding ShipPostalCode}" Header="Ship Postal Code" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipRegionColumn" Binding="{Binding ShipRegion}" Header="Ship Region" Width="SizeToHeader"/>  
             <DataGridTextColumn x:Name="shipViaColumn" Binding="{Binding ShipVia}" Header="Ship Via" Width="SizeToHeader"/>  
         </DataGrid.Columns>  
     </DataGrid>  
 </Grid>  
```  
  
## <a name="add-buttons-to-navigate-add-update-and-delete"></a>이동, 추가, 업데이트 및 삭제 하는 단추 추가  
 Windows Forms 응용 프로그램에서 데이터베이스의 행을 이동 하 고 기본적인 CRUD 작업 수행에 대 한 단추를 사용 하 여을 BindingNavigator 개체를 가져옵니다. WPF는 BindingNavigator 제공 하지는 않지만 간편 하 게 만들는 합니다. 페이지 그리드의 아래쪽 행에 가로 StackPanel 내에서 단추를 사용 하 여 로그인 할 수 있습니다 및 코드 숨김의 메서드에 바인딩되는 명령을 사용 하 여 단추를 연결 합니다.  
  
 명령 논리에서는 부분이 있습니다. (1) 명령, (2) 바인딩, (3) 단추 및 코드 숨김에서 명령 처리기 (4).  
  
#### <a name="add-commands-bindings-and-buttons-in-xaml"></a>XAML에서 명령, 바인딩 및 단추 추가  
  
1. 먼저 Windows.Resources 요소 내에서 MainWindow.XAML 파일의 명령을 추가 해 보겠습니다.  
  
    ```xaml  
  
     <RoutedUICommand x:Key="FirstCommand" Text="First"/>  
    <RoutedUICommand x:Key="LastCommand" Text="Last"/>  
    <RoutedUICommand x:Key="NextCommand" Text="Next"/>  
    <RoutedUICommand x:Key="PreviousCommand" Text="Previous"/>  
    <RoutedUICommand x:Key="DeleteCustomerCommand" Text="Delete Customer"/>  
    <RoutedUICommand x:Key="DeleteOrderCommand" Text="Delete Order"/>  
    <RoutedUICommand x:Key="UpdateCommand" Text="Update"/>  
    <RoutedUICommand x:Key="AddCommand" Text="Add"/>  
    <RoutedUICommand x:Key="CancelCommand" Text="Cancel"/>  
    ```  
  
2. CommandBinding은 RoutedUICommand 이벤트를 코드 숨김의 메서드에 매핑됩니다. 닫는 태그 Windows.Resources 뒤이 CommandBindings 요소를 추가 합니다.  
  
    ```xaml  
  
        <Window.CommandBindings>  
        <CommandBinding Command="{StaticResource FirstCommand}" Executed="FirstCommandHandler"/>  
        <CommandBinding Command="{StaticResource LastCommand}" Executed="LastCommandHandler"/>  
        <CommandBinding Command="{StaticResource NextCommand}" Executed="NextCommandHandler"/>  
        <CommandBinding Command="{StaticResource PreviousCommand}" Executed="PreviousCommandHandler"/>  
        <CommandBinding Command="{StaticResource DeleteCustomerCommand}" Executed="DeleteCustomerCommandHandler"/>  
        <CommandBinding Command="{StaticResource DeleteOrderCommand}" Executed="DeleteOrderCommandHandler"/>  
        <CommandBinding Command="{StaticResource UpdateCommand}" Executed="UpdateCommandHandler"/>  
        <CommandBinding Command="{StaticResource AddCommand}" Executed="AddCommandHandler"/>  
        <CommandBinding Command="{StaticResource CancelCommand}" Executed="CancelCommandHandler"/>  
    </Window.CommandBindings>  
    ```  
  
3. 이제 보겠습니다 탐색을 사용 하 여 StackPanel 추가, 추가, 삭제 및 단추를 업데이트 합니다. 먼저, Windows.Resources에이 스타일을 추가 합니다.  
  
    ```xaml  
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">  
        <Setter Property="FontSize" Value="24"/>  
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>  
        <Setter Property="Margin" Value="2,2,2,0"/>  
        <Setter Property="Width" Value="40"/>  
        <Setter Property="Height" Value="auto"/>  
    </Style>  
    ```  
  
     XAML 페이지의 위쪽 외부 표 요소에 대 한 RowDefinitions 직후 이제이 코드를 붙여 넣습니다.  
  
    ```xaml  
    <StackPanel  Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">  
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"  />  
        <Button Name="btnPrev"  Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnNext"  Content="►" Command="{StaticResource NextCommand}"     Style="{StaticResource NavButton}"/>  
        <Button Name="btnLast"  Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>  
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>  
        <Button  Name="btnAdd"   Content="New Customer"  Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>  
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
        <Button Content="Cancel" Name="btnCancel"  Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>  
    </StackPanel>  
    ```  
  
#### <a name="add-command-handlers-to-the-mainwindow-class"></a>MainWindow 클래스에 명령 처리기를 추가 합니다.  
  
1. 코드 숨김을 추가 및 삭제 메서드를 제외 하 고 최소화 됩니다. 탐색 CollectionViewSource의 뷰 속성에서 메서드를 호출 하 여 수행 되는 참고 합니다. DeleteOrderCommandHandler 주문에 계단식 삭제를 수행 하는 방법을 보여 줍니다. 연관 된 Order_Details를 먼저 삭제 해야 합니다. UpdateCommandHandler 컬렉션에 새 고객을 추가 합니다. 그러지 않으면만 사용 하 여 텍스트 상자에 대 한 사용자를 변경 하는 모든 기존 개체를 업데이트 합니다.  
  
2. 이러한 각 방법에서 이름을 조정 해야 프로그램 CollectionViewSource Customers 테이블에 대 한 다른 이름에 있는 경우 MainWindow.xaml.cs에서 MainWindow 클래스에 다음 처리기 메서드를 추가 합니다.  
  
    ```csharp  
       private void LastCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToLast();  
    }  
  
    private void PreviousCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToPrevious();  
    }  
  
    private void NextCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToNext();  
    }  
  
    private void FirstCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        custViewSource.View.MoveCurrentToFirst();  
    }  
  
    private void DeleteCustomerCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        // If existing window is visible, then delete the customer and all their orders.  
        // In a real application, you should add warnings and allow a user to cancel the operation.  
        var cur = custViewSource.View.CurrentItem as Customer;  
  
        var cust = (from c in context.Customers  
                    where c.CustomerID == cur.CustomerID  
                    select c).FirstOrDefault();  
  
        if (cust != null)  
        {  
            foreach (var ord in cust.Orders.ToList())  
            {  
                Delete_Order(ord);  
            }  
            context.Customers.Remove(cust);  
        }  
        context.SaveChanges();  
        custViewSource.View.Refresh();  
    }  
  
    // Commit changes from the new customer form, the new order form,  
    // or edits made to the existing customer form.  
    private void UpdateCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        if (newCustomerGrid.IsVisible)  
        {  
            // Create a new object because the old one  
            // is being tracked by EF now.  
            newCustomer = new Customer();   
            newCustomer.Address = add_addressTextBox.Text;  
            newCustomer.City = add_cityTextBox.Text;  
            newCustomer.CompanyName = add_companyNameTextBox.Text;  
            newCustomer.ContactName = add_contactNameTextBox.Text;  
            newCustomer.ContactTitle = add_contactTitleTextBox.Text;  
            newCustomer.Country = add_countryTextBox.Text;  
            newCustomer.CustomerID = add_customerIDTextBox.Text;  
            newCustomer.Fax = add_faxTextBox.Text;  
            newCustomer.Phone = add_phoneTextBox.Text;  
            newCustomer.PostalCode = add_postalCodeTextBox.Text;  
            newCustomer.Region = add_regionTextBox.Text;  
  
            // Perform very basic validation  
            if (newCustomer.CustomerID.Length == 5)  
            {  
                // Insert the new customer at correct position:  
                int len = context.Customers.Local.Count();  
                int pos = len;  
                for (int i = 0; i < len; ++i)  
                {  
                    if (String.CompareOrdinal(newCustomer.CustomerID, context.Customers.Local[i].CustomerID) < 0)  
                    {  
                        pos = i;  
                        break;  
                    }  
                }  
                context.Customers.Local.Insert(pos, newCustomer);  
                custViewSource.View.Refresh();  
                custViewSource.View.MoveCurrentTo(newCustomer);  
            }  
            else  
            {  
                MessageBox.Show("CustomerID must have 5 characters.");  
            }  
  
            newCustomerGrid.Visibility = Visibility.Collapsed;  
            existingCustomerGrid.Visibility = Visibility.Visible;  
        }  
        else if (newOrderGrid.IsVisible)  
        {  
            // Order ID is auto-generated so we don't set it here.  
            // For CustomerID, address, etc we use the values from current customer.  
            // User can modify these in the datagrid after the order is entered.  
  
            newOrder.OrderDate = add_orderDatePicker.SelectedDate;  
            newOrder.RequiredDate = add_requiredDatePicker.SelectedDate;  
            newOrder.ShippedDate = add_shippedDatePicker.SelectedDate;  
            try  
            {  
                // Exercise for the reader if you are using Northwind:  
                // Add the Northwind Shippers table to the model.  
                // Acceptable ShipperID values are 1, 2, or 3.  
                if (add_ShipViaTextBox.Text == "1" || add_ShipViaTextBox.Text == "2"  
                    || add_ShipViaTextBox.Text == "3")  
                {  
                    newOrder.ShipVia = Convert.ToInt32(add_ShipViaTextBox.Text);  
                }  
                else  
                {  
                    MessageBox.Show("Shipper ID must be 1, 2, or 3 in Northwind.");  
                    return;  
                }  
            }  
            catch  
            {  
                MessageBox.Show("Ship Via must be convertible to int");  
                return;  
            }  
            try  
            {  
                newOrder.Freight = Convert.ToDecimal(add_freightTextBox.Text);  
            }  
            catch  
            {  
                MessageBox.Show("Freight must be convertible to decimal.");  
                return;  
            }  
  
            // Add the order into the EF model  
            context.Orders.Add(newOrder);  
            ordViewSource.View.Refresh();  
        }  
  
        // Save the changes, either for a new customer, a new order  
        // or an edit in an existing customer or order  
        context.SaveChanges();  
    }  
  
    // Sets up the form so that user can enter data. Data is later  
    // saved when user clicks Commit.  
    private void AddCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        existingCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.Visibility = Visibility.Collapsed;  
        newCustomerGrid.Visibility = Visibility.Visible;  
  
        // Clear all the text boxes before adding a new customer.  
        foreach (var child in newCustomerGrid.Children)  
        {  
            var tb = child as TextBox;  
            if (tb != null)  
            {  
                tb.Text = "";  
            }  
        }  
    }  
  
    private void NewOrder_click(object sender, RoutedEventArgs e)  
    {  
        var cust = custViewSource.View.CurrentItem as Customer;  
        if (cust == null)  
        {  
            MessageBox.Show("No customer selected.");  
            return;  
        }  
  
        newOrder.CustomerID = cust.CustomerID;  
  
        // Get address and other mostly constant fields from   
        // an existing order, if one exists  
        var coll = custViewSource.Source as IEnumerable<Customer>;  
        var lastOrder = (from c in coll  
                         from ord in c.Orders  
                         select ord).LastOrDefault();  
        if (lastOrder != null)  
        {  
            newOrder.ShipAddress = lastOrder.ShipAddress;  
            newOrder.ShipCity = lastOrder.ShipCity;  
            newOrder.ShipCountry = lastOrder.ShipCountry;  
            newOrder.ShipName = lastOrder.ShipName;  
            newOrder.ShipPostalCode = lastOrder.ShipPostalCode;  
            newOrder.ShipRegion = lastOrder.ShipRegion;  
        }  
  
        existingCustomerGrid.Visibility = Visibility.Collapsed;  
        newCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.UpdateLayout();  
        newOrderGrid.Visibility = Visibility.Visible;  
    }  
  
    // Cancels any input into the new customer form  
    private void CancelCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        add_addressTextBox.Text = "";  
        add_cityTextBox.Text = "";  
        add_companyNameTextBox.Text = "";  
        add_contactNameTextBox.Text = "";  
        add_contactTitleTextBox.Text = "";  
        add_countryTextBox.Text = "";  
        add_customerIDTextBox.Text = "";  
        add_faxTextBox.Text = "";  
        add_phoneTextBox.Text = "";  
        add_postalCodeTextBox.Text = "";  
        add_regionTextBox.Text = "";  
  
        existingCustomerGrid.Visibility = Visibility.Visible;  
        newCustomerGrid.Visibility = Visibility.Collapsed;  
        newOrderGrid.Visibility = Visibility.Collapsed;  
    }  
  
    private void Delete_Order(Order order)  
    {  
        // Find the order in the EF model.  
        var ord = (from o in context.Orders.Local  
                   where o.OrderID == order.OrderID  
                   select o).FirstOrDefault();  
  
        // Delete all the order_details that have  
        // this Order as a foreign key  
        foreach (var detail in ord.Order_Details.ToList())  
        {  
            context.Order_Details.Remove(detail);  
        }  
  
        // Now it's safe to delete the order.  
        context.Orders.Remove(ord);  
        context.SaveChanges();  
  
        // Update the data grid.  
        ordViewSource.View.Refresh();  
    }  
  
    private void DeleteOrderCommandHandler(object sender, ExecutedRoutedEventArgs e)  
    {  
        // Get the Order in the row in which the Delete button was clicked.  
        Order obj = e.Parameter as Order;  
        Delete_Order(obj);  
    }  
    ```  
  
3. **F5**키를 누릅니다. 데이터를 표시 하 고 탐색 단추는 예상 대로 작동 해야 합니다. "커밋" 데이터를 입력 한 후 모델에 새 고객 또는 주문과 추가 하려면 클릭 합니다.  "취소"를 저장 하지 않고 새 고객 또는 새 주문을 폼에서 다시 클릭 합니다. 편집 기존 고객과 텍스트 상자에 직접 주문 하 고 해당 변경 내용을 모델에 자동으로 작성 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [.NET 용 visual Studio data tools](../data-tools/visual-studio-data-tools-for-dotnet.md) [Entity Framework 설명서](https://msdn.microsoft.com/data/ee712907.aspx)
