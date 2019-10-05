---
title: WPF 및 Entity Framework 6을 사용 하 여 간단한 데이터 응용 프로그램
ms.date: 08/22/2017
ms.topic: conceptual
dev_langs:
- CSharp
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d67ca69856f48ec916f27498798cbb58efb3e5ac
ms.sourcegitcommit: 13ab9a5ab039b070b9cd9251d0b83dd216477203
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66177375"
---
# <a name="create-a-simple-data-application-with-wpf-and-entity-framework-6"></a>WPF 및 Entity Framework 6을 사용하여 간단한 데이터 애플리케이션 만들기

이 연습에는 Visual Studio에서 기본 "데이터 폼" 응용 프로그램을 만드는 방법을 보여 줍니다. 앱에서는 SQL Server LocalDB, Northwind 데이터베이스, Entity Framework 6 및 Windows Presentation Foundation을 사용합니다. 마스터-세부 뷰를 사용 하 여 기본 데이터 바인딩 작업을 수행 하는 방법을 보여 줍니다 및 단추를 사용 하 여 사용자 지정 바인딩 탐색기 역시 **다음으로 이동**를 **이전으로 이동**, **부터이동**하십시오 **끝으로 이동**를 **업데이트** 및 **삭제**합니다.

이 문서에서는 Visual Studio에서 데이터 도구를 사용 하 여에 중점을 둡니다 및 모든 수준에서 기본 기술에 설명 하려고 하지 않습니다. XAML, Entity Framework 및 SQL에 대 한 기본 지식이 있다고 가정 합니다. 또한이 예제에서는 WPF 응용 프로그램에 대 한 표준 모델-뷰-ViewModel (MVVM) 아키텍처를 보여 주지 않습니다. 그러나이 코드를 약간만 수정 하 여 MVVM 응용 프로그램 자체에 복사할 수 있습니다.

## <a name="install-and-connect-to-northwind"></a>설치 하 고 Northwind로 연결

이 예제에서는 Northwind 샘플 데이터베이스 및 SQL Server Express LocalDB를 사용 합니다. 해당 제품에 대 한 ADO.NET 데이터 공급자가 Entity Framework를 지 원하는 다른 SQL 데이터베이스 제품과 마찬가지로 작동 합니다.

1. SQL Server Express LocalDB가 없는 경우 설치에서 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express), 또는 합니다 **Visual Studio 설치 관리자**합니다. **Visual Studio 설치 관리자**에서 **.NET 데스크톱 개발** 워크로드의 일부로 또는 개별 구성 요소로서 SQL Server Express LocalDB를 설치할 수 있습니다.

2. 다음이 단계를 수행 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

    1. Visual Studio에서 엽니다는 **SQL Server 개체 탐색기** 창입니다. (**SQL Server 개체 탐색기** 의 일부로 설치 되는 **데이터 저장 및 처리** 에서 워크 로드를 **Visual Studio 설치 관리자**.) 확장 된 **SQL Server** 노드. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 선택 **새 쿼리**합니다.

       쿼리 편집기 창이 열립니다.

    2. 복사 합니다 [Northwind Transact SQL 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 클립보드에 있습니다. 이 T-SQL 스크립트부터에서 Northwind 데이터베이스를 만들고 데이터로 채웁니다.

    3. T-SQL 스크립트, 쿼리 편집기에 붙여넣고 선택한 합니다 **Execute** 단추입니다.

       짧은 시간 후 쿼리 실행이 완료 하 고 Northwind 데이터베이스 생성 됩니다.

3. [새 연결 추가](../data-tools/add-new-connections.md) Northwind에 대 한 합니다.

## <a name="configure-the-project"></a>프로젝트 구성

1. Visual Studio에서 만들 새 C# **WPF 앱** 프로젝트입니다.

2. Entity Framework 6에 대 한 NuGet 패키지를 추가 합니다. **솔루션 탐색기**, 프로젝트 노드를 선택 합니다. 주 메뉴에서 선택 **프로젝트** > **NuGet 패키지 관리**합니다.

     ![NuGet 패키지 메뉴 항목 관리](../data-tools/media/raddata_vs2015_manage_nuget_packages.png)

3. 에 **NuGet 패키지 관리자**를 클릭 합니다 **찾아보기** 링크. Entity Framework 목록의 최상위 패키지 때문일 수 있습니다. 클릭 **설치** 오른쪽 창에서를 따릅니다. 설치가 완료 되 면 출력 창에서 알 수 있습니다.

     ![Entity Framework NuGet 패키지](../data-tools/media/raddata_vs2015_nuget_ef.png)

4. 이제 Northwind 데이터베이스를 기반으로 모델을 만들려면 Visual Studio를 사용할 수 있습니다.

## <a name="create-the-model"></a>모델 만들기

1. 프로젝트 노드를 마우스 오른쪽 단추로 클릭 **솔루션 탐색기** 선택한 **추가** > **새 항목**합니다. C# 노드를 아래 왼쪽된 창에서 선택 **데이터** 가운데 창에서 선택 하 고 **ADO.NET Entity Data Model**합니다.

   ![Entity Framework 모델에 대 한 새 항목](../data-tools/media/raddata-ef-new-project-item.png)

2. 모델을 호출 `Northwind_model` 선택한 **확인**합니다. **엔터티 데이터 모델 마법사**가 열립니다. 선택할 **데이터베이스의 EF 디자이너** 을 클릭 한 다음 **다음**합니다.

   ![데이터베이스에서 EF 모델](../data-tools/media/raddata-ef-model-from-database.png)

3. 다음 화면에서 LocalDB Northwind에 연결 하 고 선택 **다음**합니다.

4. 마법사의 다음 페이지에서 테이블, 저장된 프로시저 및 다른 데이터베이스에에서 포함할 개체를 Entity Framework 모델을 선택 합니다. 트리 뷰에서 dbo 노드를 확장 하 고 선택 **고객이**, **주문**, 및 **Order Details**합니다. 기본값이 선택 된 상태로 두고 클릭 **완료**합니다.

    ![모델에 대 한 데이터베이스 개체 선택](../data-tools/media/raddata-choose-ef-objects.png)

5. 마법사는 Entity Framework 모델을 나타내는 C# 클래스를 생성 합니다. 클래스는 이전 일반 C# 클래스가 고 어떻게 WPF 사용자 인터페이스에 데이터 바인딩합니다. 합니다 *.edmx* 관계 및 데이터베이스의 개체를 사용 하 여 클래스를 연결 하는 다른 메타 데이터 파일에 설명 합니다. 합니다 *.tt* 파일은 데이터베이스에 변경 내용을 저장 하 고 모델에서 작동 하는 코드를 생성 하는 T4 템플릿입니다. 이러한 모든 파일을 볼 수 있습니다 **솔루션 탐색기** Northwind_model 노드 아래에서:

      ![솔루션 탐색기 EF 모델 파일](../data-tools/media/raddata-solution-explorer-ef-model-files.png)

    디자이너 화면에 대 한 합니다 *.edmx* 파일을 사용 하면 일부 속성 및 모델의 관계를 수정할 수 있습니다. 디자이너를 사용 하 여이 연습을 하지 않습니다.

6. 합니다 *.tt* 파일은 범용 및 ObservableCollections 하며 WPF 데이터 바인딩 작업 중 하나를 조정 해야 합니다. **솔루션 탐색기**를 찾을 때까지 Northwind_model 노드를 확장 *Northwind_model.tt*합니다. (아닌 있는지 확인 합니다 *합니다. Context.tt* 파일을 바로 아래에 *.edmx* 파일입니다.)

   - 두 바꿀 <xref:System.Collections.ICollection> 사용 하 여 <xref:System.Collections.ObjectModel.ObservableCollection%601>입니다.

   - 첫 번째 항목을 바꾸려면 <xref:System.Collections.Generic.HashSet%601> 사용 하 여 <xref:System.Collections.ObjectModel.ObservableCollection%601> 51 줄. HashSet의 두 번째 발생을 대체 하지 않습니다.

   - 유일한 대체할 <xref:System.Collections.Generic> (줄 근처 431) 사용 하 여 <xref:System.Collections.ObjectModel>입니다.

7. 키를 눌러 **Ctrl**+**Shift**+**B** 프로젝트를 빌드합니다. 빌드가 완료 되 면 모델 클래스는 데이터 원본 마법사에 표시 합니다.

이제 XAML 페이지에이 모델을 보고, 탐색 및 데이터를 수정할 수 있도록 후크 준비가 되었습니다.

## <a name="databind-the-model-to-the-xaml-page"></a>Databind XAML 페이지 모델

사용자 고유의 데이터 바인딩 코드를 작성할 수 있지만 Visual Studio 작업을 수행할 수 있도록 훨씬 쉽습니다.

1. 주 메뉴에서 선택 **프로젝트** > **새 데이터 원본 추가** 불러오려면 합니다 **데이터 소스 구성 마법사**합니다. 선택할 **개체** 바인딩하게 되므로 모델 클래스, 데이터베이스에 없습니다.

     ![개체 소스를 사용 하 여 데이터 소스 구성 마법사](../data-tools/media/raddata-data-source-configuration-wizard-with-object-source.png)

2. 선택 **고객**합니다. (원본 주문에 대 한 고객의 주문 탐색 속성에서 자동으로 생성 됩니다.)

     ![데이터 원본으로 엔터티 클래스를 추가 합니다.](../data-tools/media/raddata-add-entity-classes-as-data-sources.png)

3. **마침**을 클릭합니다.

4. 이동할 *MainWindow.xaml* 코드 보기에서. 이 예제의 목적에는 XAML을 단순하게 유지 하 고 했습니다. 좀 더 구체적인 MainWindow의 제목을 변경 하 고 지금은 600 x 800로 해당 높이 너비를 늘립니다. 항상 변경할 수 있습니다 하 나중입니다. 이제 이러한 세 가지 행 정의 주 표 형태의 탐색 단추, 하나는 고객의 세부 정보 및 고객의 주문을 보여 주는 눈금에 대 한 하나의 행을 추가 합니다.

    ```xaml
    <Grid.RowDefinitions>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="auto"/>
            <RowDefinition Height="*"/>
        </Grid.RowDefinitions>
    ```

5. 이제 열 *MainWindow.xaml* 디자이너에서 보고 있는 되도록 합니다. 이 인해 합니다 **데이터 원본** 창 옆에 Visual Studio 창 여백에 옵션으로 표시 하는 **도구 상자**합니다. 창을 열거나 다른 키를 눌러 탭을 클릭 **Shift**+**Alt**+**D** 선택할지 **보기**  >  **다른 Windows** > **데이터 원본**합니다. 고객은 클래스 자체의 개별 텍스트 상자에서 각 속성을 표시 하려고 합니다. 먼저, 화살표를 클릭 합니다 **고객이** 콤보 확인란을 선택한 **세부 정보**합니다. 그런 다음 디자이너 가운데 행에서 이동 하려는 알 수 있도록 디자인 화면의 가운데 부분에 노드를 끕니다. 이 잃어 버리면 하는 경우에 XAML에서 나중에 수동으로 행을 지정할 수 있습니다. 기본적으로 세로 그리드 요소에 배치 된 하지만 시점에서 정렬할 수 폼에서 원하는 합니다. 예를 들어, 배치 하는 것이 해야 합니다 **이름을** 주소 위에서 위쪽의 텍스트 상자입니다. 이 문서에 대 한 샘플 응용 프로그램 필드 다시 정렬 하 고 이러한 두 개의 열으로 다시 정렬.

     ![개별 컨트롤에 고객 데이터 소스 바인딩](../data-tools/media/raddata-customers-data-source-binding-to-individual-controls.png)

     코드 보기에서 이제 볼 수 있습니다 새 `Grid` 행의 요소 1 (중간 행)의 부모 표입니다. 눈금에 부모를 `DataContext` 에 추가 된 collectionviewsource에 바인딩하면 참조 특성을 `Windows.Resources` 요소입니다. 해당 데이터 컨텍스트를 지정 하 여 첫 번째 텍스트 상자에 바인딩할 때 **주소**, 해당 이름에 매핑되는 `Address` 현재에서 속성 `Customer` CollectionViewSource에 개체입니다.

    ```xaml
    <Grid DataContext="{StaticResource customerViewSource}">
    ```

6. 고객 창의 위쪽에 표시 되 면 아래에 있는 고객의 주문을 반 참조 하려고 합니다. 단일 표 뷰 컨트롤에서 주문을 표시 합니다. 예상 대로 작동 하는 마스터-세부 데이터 바인딩, 별도 Orders 노드 필요가 고객 클래스에 Orders 속성에 바인딩하는 것이 중요 한 것입니다. 디자이너 2 행에 저장 되도록 폼의 아래쪽 절반을 고객에 게 클래스의 Orders 속성으로를 끕니다.

     ![그리드로 끌어 Orders 클래스](../data-tools/media/raddata-drag-orders-classes-as-grid.png)

7. Visual Studio UI 컨트롤 모델에서 이벤트에 연결 하는 모든 바인딩 코드를 생성 했습니다. 일부 데이터를 확인 하기 위해 수행 해야 하는 모든 모델을 채우는 코드를 작성 하는 것입니다. 먼저 이동할 *MainWindow.xaml.cs* 데이터 컨텍스트에 대해 MainWindow 클래스에 데이터 멤버를 추가 합니다. 이 개체를 생성 된 변경 내용 및 모델에서 이벤트를 추적 하는 컨트롤 같이 작동 합니다. 생성자 초기화 논리를 추가할 수도 있습니다. 클래스의 맨 위에 다음과 같이 표시 됩니다.

     [!code-csharp[MainWindow#1](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#1)]

     추가 된 `using` System.Data.Entity Load 확장 메서드를 범위로 가져올에 대 한 지시문:

     ```csharp
     using System.Data.Entity;
     ```

     이제 아래로 스크롤하여 찾을 `Window_Loaded` 이벤트 처리기입니다. Visual Studio가 CollectionViewSource 개체를 추가 되었습니다 확인 합니다. 이 모델을 만들 때 선택한 NorthwindEntities 개체를 나타냅니다. 코드를 추가 해 보겠습니다 `Window_Loaded` 전체 메서드는 이제 다음과 같이 표시 되도록 합니다.

     [!code-csharp[Window_Loaded#2](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#2)]

8. **F5**키를 누릅니다. CollectionViewSource에 검색 된 첫 번째 고객에 대 한 세부 정보가 표시 됩니다. 데이터 그리드에서 해당 주문도 표시 됩니다. 서식 지정 하겠습니다 픽스업 하는 훌륭한 아닙니다. 또한 다른 레코드를 확인 하 고 기본 CRUD 작업을 수행 하는 방법을 만들 수 있습니다.

## <a name="adjust-the-page-design-and-add-grids-for-new-customers-and-orders"></a>페이지 디자인을 조정 하 고 새로운 고객 및 주문에 대 한 표 추가

Visual Studio에서 생성 된 기본 배열을 변경 일부 수동으로 XAML에 있으므로 응용 프로그램에 적합 하지 않습니다. 또한 일부 "forms" (임, 실제로 표)는 새 고객 또는 주문과 추가할 사용자를 사용 하도록 설정 해야 합니다. 텍스트 상자에 데이터 바인딩된 없는 별도 집합을 새 customer와 order를 추가할 수 있도록 해야 합니다 `CollectionViewSource`합니다. Visible 속성 처리기 메서드를 설정 하 여 언제 든 지 사용자에 게는 표를 제어할 수 있습니다. 마지막으로, 개별 주문을 삭제 하려면 사용자를 사용 하도록 설정 하려면 주문 표의 각 행에 삭제 단추를 추가 합니다.

먼저, 이러한 스타일을 추가 합니다 `Windows.Resources` 요소에 *MainWindow.xaml*:

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
<Grid>
     <Grid.RowDefinitions>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="auto"/>
         <RowDefinition Height="*"/>
     </Grid.RowDefinitions>
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
         <TextBox x:Name="customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
         <TextBox x:Name="add_customerIDTextBox" Grid.Row="0" Style="{StaticResource CustTextBox}"
                  Text="{Binding CustomerID, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Company Name:" Grid.Row="1" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_companyNameTextBox" Grid.Row="1" Style="{StaticResource CustTextBox}"
                  Text="{Binding CompanyName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true }"/>
         <Label Content="Contact Name:" Grid.Row="2" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactNameTextBox" Grid.Row="2" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactName, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Contact title:" Grid.Row="3" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_contactTitleTextBox" Grid.Row="3" Style="{StaticResource CustTextBox}"
                  Text="{Binding ContactTitle, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="Address:" Grid.Row="4" Style="{StaticResource Label}"/>
         <TextBox x:Name="add_addressTextBox" Grid.Row="4" Style="{StaticResource CustTextBox}"
                  Text="{Binding Address, Mode=TwoWay, NotifyOnValidationError=true, ValidatesOnExceptions=true}"/>
         <Label Content="City:" Grid.Column="1" Grid.Row="0" Style="{StaticResource Label}"/>
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
                         <Button Content="Delete" Command="{StaticResource DeleteOrderCommand}" CommandParameter="{Binding}"/>
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

Windows Forms 응용 프로그램에서 데이터베이스의 행을 이동 하 고 기본적인 CRUD 작업 수행에 대 한 단추를 사용 하 여을 BindingNavigator 개체를 가져옵니다. WPF는 BindingNavigator를 제공 하지 않습니다 하지만 쉽게 만드세요. 가로 StackPanel 내에서 단추를 사용 하 여 작업을 수행 하 고이 정보를 코드 숨김의 메서드에 바인딩되는 명령 단추를 연결 합니다.

명령 논리에서는 부분이 있습니다. (1) 명령, (2) 바인딩, (3) 단추 및 코드 숨김에서 명령 처리기 (4).

### <a name="add-commands-bindings-and-buttons-in-xaml"></a>XAML에서 명령, 바인딩 및 단추 추가

1. 먼저 명령에 추가 합니다 *MainWindow.xaml* 파일을 `Windows.Resources` 요소:

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

2. CommandBinding 매핑하는 `RoutedUICommand` 코드 숨김의 메서드는 이벤트입니다. 이 추가 `CommandBindings` 요소 뒤의 `Windows.Resources` 닫는 태그:

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

3. 이제 추가 `StackPanel` 의 탐색을 사용 하 여 추가, 삭제 및 단추를 업데이트 합니다. 이 스타일을 먼저 추가 `Windows.Resources`:

    ```xaml
    <Style x:Key="NavButton" TargetType="{x:Type Button}" BasedOn="{x:Null}">
        <Setter Property="FontSize" Value="24"/>
        <Setter Property="FontFamily" Value="Segoe UI Symbol"/>
        <Setter Property="Margin" Value="2,2,2,0"/>
        <Setter Property="Width" Value="40"/>
        <Setter Property="Height" Value="auto"/>
    </Style>
    ```

     둘째,이 코드를 붙여 바로 뒤의 `RowDefinitions` 외부 `Grid` XAML 페이지의 맨 위에 요소:

    ```xaml
    <StackPanel Orientation="Horizontal" Margin="2,2,2,0" Height="36" VerticalAlignment="Top" Background="Gainsboro" DataContext="{StaticResource customerViewSource}" d:LayoutOverrides="LeftMargin, RightMargin, TopMargin, BottomMargin">
        <Button Name="btnFirst" Content="|◄" Command="{StaticResource FirstCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnPrev" Content="◄" Command="{StaticResource PreviousCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnNext" Content="►" Command="{StaticResource NextCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnLast" Content="►|" Command="{StaticResource LastCommand}" Style="{StaticResource NavButton}"/>
        <Button Name="btnDelete" Content="Delete Customer" Command="{StaticResource DeleteCustomerCommand}" FontSize="11" Width="120" Style="{StaticResource NavButton}"/>
        <Button Name="btnAdd" Content="New Customer" Command="{StaticResource AddCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="New Order" Name="btnNewOrder" FontSize="11" Width="80" Style="{StaticResource NavButton}" Click="NewOrder_click"/>
        <Button Name="btnUpdate" Content="Commit" Command="{StaticResource UpdateCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
        <Button Content="Cancel" Name="btnCancel" Command="{StaticResource CancelCommand}" FontSize="11" Width="80" Style="{StaticResource NavButton}"/>
    </StackPanel>
    ```

### <a name="add-command-handlers-to-the-mainwindow-class"></a>MainWindow 클래스에 명령 처리기를 추가 합니다.

코드 숨김을 추가 및 삭제 메서드를 제외 하 고 최소화 됩니다. 탐색은 CollectionViewSource의 뷰 속성에서 메서드를 호출 하 여 수행 됩니다. `DeleteOrderCommandHandler` 주문에서 계단식 삭제를 수행 하는 방법을 보여 줍니다. 연관 된 Order_Details를 먼저 삭제 해야 합니다. `UpdateCommandHandler` 만 사용자가 텍스트 상자에 대 한 변경 내용으로는 기존 고객 또는 주문과 업데이트. 그렇지 않으면 새 고객 또는 주문 컬렉션에 추가 합니다.

이러한 처리기 메서드를 MainWindow 클래스에 추가 *MainWindow.xaml.cs*합니다. Customers 테이블에 대 한 CollectionViewSource에 이름이 다른 경우에서 이러한 각 메서드 이름을 조정 해야 다음:

[!code-csharp[CommandHandlers#3](../data-tools/codesnippet/CSharp/CreateWPFDataApp/MainWindow.xaml.cs#3)]

## <a name="run-the-application"></a>애플리케이션 실행

디버깅을 시작하려면 **F5** 키를 누릅니다. 고객 및 표의 채워진 주문 데이터가 표시 되어야 하 고 탐색 단추는 예상 대로 작동 해야 합니다. 클릭할 **커밋** 데이터를 입력 한 후 모델에 새 고객 또는 주문과 추가 합니다. 클릭할 **취소** 데이터를 저장 하지 않고 새 고객 또는 새 주문 양식에서 백업할 수 있습니다. 기존 고객 및 주문 입력란에서 직접 편집할 수 있습니다 하 고 해당 변경 내용을 모델에 자동으로 작성 됩니다.

## <a name="see-also"></a>참고자료

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Entity Framework 설명서](/ef/)