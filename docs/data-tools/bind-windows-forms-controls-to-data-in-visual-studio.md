---
title: 데이터에 Windows Forms 컨트롤 바인딩
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- data [Windows Forms], data sources
- Windows Forms, data binding
- Windows Forms, displaying data
- displaying data on forms
- forms, displaying data
- data sources, displaying data
- displaying data, Windows Forms
- data [Windows Forms], displaying
ms.assetid: 243338ef-41af-4cc5-aff7-1e830236f0ec
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6b961af0bf35bb4476f9f336fcf5298bb0bd3651
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62818772"
---
# <a name="bind-windows-forms-controls-to-data-in-visual-studio"></a>Windows Forms 컨트롤을 Visual Studio의 데이터에 바인딩

Windows Forms에 데이터를 바인딩하여 응용 프로그램의 사용자에 게 데이터를 표시할 수 있습니다. 이러한 데이터 바인딩된 컨트롤을 만들려면 항목을 끌어 놓아 합니다 **데이터 원본** Visual Studio에서 Windows Forms 디자이너 창.

![데이터 원본 끌기 작업](../data-tools/media/raddata-data-source-drag-operation.png)

> [!TIP]
> 경우는 **데이터 원본** 창이 표시 되지 않으면, 선택 하 여 열 수 있습니다 **뷰** > **기타 Windows** > **데이터 원본** , 또는 키를 눌러 **Shift**+**Alt**+**D**합니다. 보려면 Visual Studio에서 프로젝트가 열려 있어야 합니다 **데이터 원본** 창입니다.

항목을 끌면 전에에 바인딩할 컨트롤의 형식을 설정할 수 있습니다. 다른 값 자체 또는 개별 열 테이블을 선택 하는지 여부에 따라 표시 됩니다.  또한 사용자 지정 값을 설정할 수 있습니다. 테이블에 대해 **세부 정보** 각 열을 별도 컨트롤에 바인딩되어 있음을 의미 합니다.

![DataGridView에 데이터 소스 바인딩](../data-tools/media/raddata-bind-data-source-to-datagridview.png)

## <a name="bindingsource-and-bindingnavigator-controls"></a>BindingSource 및 BindingNavigator 컨트롤

<xref:System.Windows.Forms.BindingSource> 구성 요소는 두가지 용도로 사용됩니다. 먼저 데이터를 컨트롤에 바인딩할 때 추상화 계층을 제공 합니다. 폼의 컨트롤에 바인딩된는 <xref:System.Windows.Forms.BindingSource> 데이터 원본에 직접 대신 구성 요소입니다. 둘째,이 개체의 컬렉션을 관리할 수 있습니다. 에 형식을 추가 합니다 <xref:System.Windows.Forms.BindingSource> 해당 형식의 목록을 만듭니다.

에 대 한 자세한 내용은 <xref:System.Windows.Forms.BindingSource> 구성 요소를 참조 하세요.

- [BindingSource 구성 요소](/dotnet/framework/winforms/controls/bindingsource-component)

- [BindingSource 구성 요소 개요](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- [BindingSource 구성 요소 아키텍처](/dotnet/framework/winforms/controls/bindingsource-component-architecture)

합니다 [BindingNavigator 컨트롤](/dotnet/framework/winforms/controls/bindingnavigator-control-windows-forms) Windows 응용 프로그램에서 표시 되는 데이터를 탐색 하기 위한 사용자 인터페이스를 제공 합니다.

## <a name="bind-to-data-in-a-datagridview-control"></a>DataGridView 컨트롤의 데이터에 바인딩

에 대 한는 [DataGridView 컨트롤](/dotnet/framework/winforms/controls/datagridview-control-overview-windows-forms), 전체 테이블이 단일 해당 컨트롤에 바인딩되어 있습니다. 끌면를 **DataGridView** 폼에 레코드를 탐색 하기 위한 도구 제거 (<xref:System.Windows.Forms.BindingNavigator>)도 표시 됩니다. A [데이터 집합](../data-tools/dataset-tools-in-visual-studio.md)를 [TableAdapter](../data-tools/create-and-configure-tableadapters.md)를 <xref:System.Windows.Forms.BindingSource>, 및 <xref:System.Windows.Forms.BindingNavigator> 구성 요소 트레이에 나타납니다. 다음 그림에는 [TableAdapterManager](https://msdn.microsoft.com/library/bb384426.aspx) Customers 테이블에 Orders 테이블 관계가 있으므로 추가 됩니다. 이러한 변수는 선언 된 모든 자동 생성 코드에서 폼 클래스의 private 멤버. 채우기의 자동 생성 된 코드를 **DataGridView** 에 `Form_Load` 이벤트 처리기입니다. 데이터베이스를 업데이트 하려면 데이터를 저장할 코드에는 `Save` 에 대 한 이벤트 처리기는 **BindingNavigator**합니다. 이동 하거나 필요에 따라이 코드를 수정할 수 있습니다.

![BindingNavigator 사용 하 여 GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png)

동작을 사용자 지정할 수는 **DataGridView** 하며 **BindingNavigator** 각각의 오른쪽 위 모서리에 있는 스마트 태그를 클릭 하 여:

![DataGridView 및 바인딩 Navigator 스마트 태그](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png)

컨트롤은 응용 프로그램 필요 없는 경우 내에서 사용할 수는 **데이터 원본** 창 컨트롤을 추가할 수 있습니다. 자세한 내용은 [데이터 소스 창에 사용자 지정 컨트롤을 추가할](../data-tools/add-custom-controls-to-the-data-sources-window.md)합니다.

항목을 끌 수도 있습니다는 **데이터 원본** 이미 데이터에 컨트롤을 바인딩할 양식의 컨트롤에 창. 이미 데이터에 바인딩되는 컨트롤에 가장 최근에 끌어 항목에 바인딩됩니다. 유효한 놓기 대상 되도록 컨트롤 수 있어야에서 끌어 끌어 온 항목의 기본 데이터 형식을 표시 합니다 **데이터 원본** 창입니다. 예를 들어 유효 하지 않은 데이터 형식이 있는 항목을 끌기 <xref:System.DateTime> 에 <xref:System.Windows.Forms.CheckBox>이므로 <xref:System.Windows.Forms.CheckBox> 날짜를 표시할 수 없습니다.

## <a name="bind-to-data-in-individual-controls"></a>개별 컨트롤에 데이터 바인딩

데이터 소스를 바인딩하는 경우 **세부 정보**, 데이터 집합의 각 열은 별도 컨트롤에 바인딩됩니다.

![데이터 원본 세부 정보에 바인딩](../data-tools/media/raddata-bind-data-source-to-details.png)

> [!IMPORTANT]
> 위의 그림에서, Orders 테이블에서가 아니라 고객 테이블의 Orders 속성에서 끌어 옵니다. 에 바인딩하여 합니다 `Customer.Orders` 속성을 탐색 명령에 대 한는 **DataGridView** 세부 사항 컨트롤이에 즉시 반영 됩니다. Orders 테이블에서 끌어온, 컨트롤은 여전히 데이터 집합에 바인딩할 수 있지만 이러한는 하지와 동기화 되지 합니다 **DataGridView**합니다.

다음 그림에서는 Customers 테이블의 Orders 속성에 바인딩된 후 폼에 추가 되는 데이터 바인딩된 컨트롤을 기본 **세부 정보** 에 **데이터 원본** 창입니다.

![Orders 테이블 바인딩 세부 정보](../data-tools/media/raddata-orders-table-bound-to-details.png)

각 컨트롤에 스마트 태그는 또한 note 합니다. 이 태그에만 해당 컨트롤에 적용 되는 사용자 지정 수 있습니다.

## <a name="see-also"></a>참고자료

- [Visual Studio의 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Windows Forms (.NET Framework)의 데이터 바인딩](/dotnet/framework/winforms/windows-forms-data-binding)