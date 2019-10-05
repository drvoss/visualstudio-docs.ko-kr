---
title: 데이터 바인딩을 사용 하 여 Windows Forms 사용자 컨트롤 만들기
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9e9f80f55aa3059cbe5c9af3b5510915f768ea20
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567639"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>복합 데이터 바인딩을 지원하는 Windows Forms 사용자 정의 컨트롤 만들기

Windows 응용 프로그램에서 폼에 데이터를 표시할 때 기존 컨트롤에서 선택할 수 있습니다 합니다 **도구 상자**합니다. 또는 응용 프로그램에 표준 컨트롤에서 사용할 수 없는 기능이 필요한 경우 사용자 지정 컨트롤을 작성할 수 있습니다. 이 연습에서는 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>를 구현하는 컨트롤을 만드는 방법을 보여줍니다. <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>를 구현하는 컨트롤은 데이터에 바인딩할 수 있는 `DataSource` 및 `DataMember` 속성을 포함합니다. 이러한 컨트롤은 <xref:System.Windows.Forms.DataGridView> 또는 <xref:System.Windows.Forms.ListBox>와 비슷합니다.

컨트롤 작성에 대 한 자세한 내용은 참조 하세요. [디자인 타임에 Windows Forms 개발 컨트롤](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)합니다.

데이터 바인딩 시나리오에 사용할 컨트롤을 작성할 때는 다음 데이터 바인딩 특성 중 하나를 구현해야 합니다.

|데이터 바인딩 특성 사용법|
| - |
|단일 데이터 열이나 속성을 표시하는 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 등의 단순 컨트롤에 대해 <xref:System.Windows.Forms.TextBox>를 구현합니다. 자세한 내용은 [단순 데이터 바인딩을 지 원하는 Windows Forms 사용자 컨트롤 만들기](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md)합니다.|
|데이터 목록 또는 테이블을 표시하는 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 등의 컨트롤에 대해 <xref:System.Windows.Forms.DataGridView>를 구현합니다. 이 연습 페이지에서 해당 프로세스에 대해 설명합니다.|
|데이터 목록 또는 테이블을 표시하는 동시에 단일 열이나 속성도 제공해야 하는 <xref:System.ComponentModel.LookupBindingPropertiesAttribute> 등의 컨트롤에 대해 <xref:System.Windows.Forms.ComboBox>를 구현합니다. 자세한 내용은 [조회 데이터 바인딩을 지 원하는 Windows Forms 사용자 컨트롤 만들기](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)합니다.|

이 연습에서는 테이블의 데이터 행을 표시하는 복합 컨트롤을 만듭니다. 이 예에서는 Northwind 샘플 데이터베이스의 `Customers` 테이블을 사용합니다. 복합 사용자 컨트롤은 사용자 지정 컨트롤의 <xref:System.Windows.Forms.DataGridView>에 Customers 테이블을 표시합니다.

이 연습에서는 알아봅니다 방법:

- 프로젝트에 새 **사용자 정의 컨트롤**을 추가합니다.

- 사용자 컨트롤을 시각적으로 디자인합니다.

- `ComplexBindingProperty` 특성을 구현합니다.

- 사용 하 여 데이터 집합을 만들 합니다 [데이터 소스 구성 마법사](../data-tools/media/data-source-configuration-wizard.png)합니다.

- 설정 합니다 **고객** 테이블에 [데이터 소스 창](add-new-data-sources.md#data-sources-window) 새 복합 컨트롤을 사용 하 합니다.

- 새 컨트롤을 **데이터 원본** 창에서 **Form1**으로 끌어 추가합니다.

## <a name="prerequisites"></a>전제 조건

이 연습에서는 Northwind 샘플 데이터베이스 및 SQL Server Express LocalDB를 사용 합니다.

1. SQL Server Express LocalDB가 없는 경우 설치에서 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express), 또는 합니다 **Visual Studio 설치 관리자**합니다. 에 **Visual Studio 설치 관리자**의 일부로 SQL Server Express LocalDB를 설치할 수 있습니다는 **데이터 저장 및 처리** 워크 로드 또는 개별 구성 요소로 합니다.

1. 다음이 단계를 수행 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

    1. Visual Studio에서 엽니다는 **SQL Server 개체 탐색기** 창입니다. (SQL Server 개체 탐색기의 일부로 설치 되는 **데이터 저장소 및 처리** Visual Studio 설치 관리자에서 작업 합니다.) 확장 된 **SQL Server** 노드. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 선택 **새 쿼리**합니다.

       쿼리 편집기 창이 열립니다.

    1. 복사 합니다 [Northwind Transact SQL 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 클립보드에 있습니다. 이 T-SQL 스크립트부터에서 Northwind 데이터베이스를 만들고 데이터로 채웁니다.

    1. T-SQL 스크립트, 쿼리 편집기에 붙여넣고 선택한 합니다 **Execute** 단추입니다.

       짧은 시간 후 쿼리 실행이 완료 하 고 Northwind 데이터베이스 생성 됩니다.

## <a name="create-a-windows-forms-app-project"></a>Windows Forms 앱 프로젝트 만들기

첫 번째 단계를 만드는 것을 **Windows Forms 앱** 프로젝트에 대 한 C# 또는 Visual Basic입니다. 프로젝트 이름을 **ComplexControlWalkthrough**로 지정합니다.

## <a name="add-a-user-control-to-the-project"></a>프로젝트에 사용자 정의 컨트롤 추가

이 연습에서 복잡 한 데이터 바인딩 가능한 컨트롤을 만들기 때문에 **사용자 정의 컨트롤**, 추가 **사용자 정의 컨트롤** 프로젝트 항목:

1. **프로젝트** 메뉴에서 **사용자 컨트롤 추가**를 선택합니다.

1. **이름** 영역에 **ComplexDataGridView**를 입력하고 **추가**를 클릭합니다.

    **ComplexDataGridView** 컨트롤이 **솔루션 탐색기**에 추가되고 디자이너에서 열립니다.

## <a name="design-the-complexdatagridview-control"></a>ComplexDataGridView 컨트롤 디자인

추가할를 <xref:System.Windows.Forms.DataGridView> 사용자 정의 컨트롤로 끌어 옵니다.을 <xref:System.Windows.Forms.DataGridView> 에서 합니다 **도구 상자** 사용자 컨트롤의 디자인 화면으로 합니다.

## <a name="add-the-required-data-binding-attribute"></a>필요한 데이터 바인딩 특성 추가

데이터 바인딩을 지원하는 복합 컨트롤에 대해 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>를 구현할 수 있습니다.

1. **ComplexDataGridView** 컨트롤을 코드 보기로 전환합니다. (**보기** 메뉴에서 **코드**를 선택합니다.)

1. `ComplexDataGridView`의 코드를 다음 코드로 바꿉니다.

    [!code-csharp[VbRaddataDisplaying#4](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.cs)]
    [!code-vb[VbRaddataDisplaying#4](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-complex-data-binding_1.vb)]

1. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

## <a name="create-a-data-source-from-your-database"></a>데이터베이스에서 데이터 원본 만들기

사용 합니다 **데이터 소스 구성** 기반으로 하는 데이터 원본을 만들려면 마법사를 `Customers` Northwind 샘플 데이터베이스의 테이블:

1. 열려는 **데이터 원본** 창에는 **데이터** 메뉴에서 클릭 **데이터 소스 표시**.

2. **데이터 원본** 창에서 **새 데이터 원본 추가**를 선택하여 **데이터 원본 구성** 마법사를 시작합니다.

3. **데이터 소스 형식 선택** 페이지에서 **데이터베이스** 를 선택하고 **다음**을 클릭합니다.

4. **데이터 연결 선택** 페이지에서 다음 중 한 가지를 수행합니다.

   - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

   - **새 연결**을 선택하여 **연결 추가/수정** 대화 상자를 시작합니다.

5. 데이터베이스에 암호가 필요하면 중요한 데이터를 포함하는 옵션을 선택한 후, **다음**을 클릭합니다.

6. 에 **응용 프로그램 구성 파일에 연결 문자열을 저장** 페이지에서 클릭 **다음**합니다.

7. **데이터베이스 개체 선택** 페이지에서 **테이블** 노드를 확장합니다.

8. `Customers` 테이블을 선택한 다음, **마침**을 클릭합니다.

   **NorthwindDataSet**가 프로젝트에 추가되고 `Customers` 테이블이 **데이터 원본** 창에 나타납니다.

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>ComplexDataGridView 컨트롤을 사용 하도록 Customers 테이블 설정

**데이터 원본** 창 내에서 항목을 폼으로 끌기 전에 만들 컨트롤을 설정할 수 있습니다.

1. 디자이너에서 **Form1**을 엽니다.

1. **데이터 원본** 창에서 **Customers** 노드를 확장합니다.

1. **Customers** 노드에서 드롭다운 화살표를 클릭하고 **Customize**를 선택합니다.

1. **데이터 UI 사용자 지정 옵션** 대화 상자의 **연결된 컨트롤** 목록에서 **ComplexDataGridView**를 선택합니다.

1. `Customers` 테이블에서 드롭다운 화살표를 클릭하고 컨트롤 목록에서 **ComplexDataGridView**를 선택합니다.

## <a name="add-controls-to-the-form"></a>폼에 컨트롤 추가

**데이터 원본** 창에서 폼으로 항목을 끌어 데이터 바인딩된 컨트롤을 만들 수 있습니다. 주 **Customers** 노드를 **데이터 원본** 창에서 폼으로 끌어서 놓습니다. 있는지 확인 합니다 **ComplexDataGridView** 컨트롤은 테이블의 데이터를 표시 하는 데 사용 합니다.

## <a name="run-the-application"></a>애플리케이션 실행

**F5** 키를 눌러 응용 프로그램을 실행합니다.

## <a name="next-steps"></a>다음 단계

애플리케이션 요구 사항에 따라 데이터 바인딩을 지원하는 컨트롤을 만든 후 몇 단계를 더 수행해야 할 수도 있습니다. 일반적으로 수행하는 몇 가지 단계는 다음과 같습니다.

- 다른 애플리케이션에서 다시 사용할 수 있도록 컨트롤 라이브러리에 사용자 지정 컨트롤을 배치합니다.

- 조회 시나리오를 지원하는 컨트롤을 만듭니다. 자세한 내용은 [조회 데이터 바인딩을 지 원하는 Windows Forms 사용자 컨트롤 만들기](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)합니다.

## <a name="see-also"></a>참고자료

- [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
- [Windows Forms 컨트롤](/dotnet/framework/winforms/controls/index)