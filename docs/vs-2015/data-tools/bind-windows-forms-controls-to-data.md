---
title: 데이터에 Windows Forms 컨트롤 바인딩 | Microsoft Docs
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
- displaying data, Windows Forms controls
- Windows Forms, displaying data
- data sources, displaying
- data [Windows Forms], displaying
ms.assetid: 0163a34a-38cb-40b9-8f38-3058a90caf21
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 3541dada6167bd2f0a95913d9ccc385dc3e5ccc3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439480"
---
# <a name="bind-windows-forms-controls-to-data"></a>데이터에 Windows Forms 컨트롤 바인딩
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

개체를 끌어 데이터 소스 컨트롤에 바인딩할 수 있습니다 합니다 **데이터 원본** Windows 폼 또는 폼에서 기존 컨트롤에 창. 항목을 끌면 전에에 바인딩할 컨트롤의 형식을 설정할 수 있습니다. 다른 값 자체 또는 개별 열 테이블을 선택 하는지 여부에 따라 표시 됩니다.  또한 사용자 지정 값을 설정할 수 있습니다. 테이블에 대해 "Details"는 각 열을 별도 컨트롤에 바인딩되어 있음을 의미 합니다.  
  
 ![DataGridView에 데이터 소스를 바인딩할](../data-tools/media/raddata-bind-data-source-to-datagridview.png "raddata DataGridView 데이터 원본 바인드")  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="bind-to--data-in-a-datagridview-control"></a>DataGridView 컨트롤의 데이터에 바인딩  
 DataGridView에 대 한 전체 테이블이 단일 해당 컨트롤에 바인딩되어 있습니다. 레코드 탐색을 위한 도구 스트립 DataGridView를 폼으로 끌면 (<xref:System.Windows.Forms.BindingNavigator>)도 표시 됩니다. A [데이터 집합](../data-tools/dataset-tools-in-visual-studio.md)에서 TableAdapter를 <xref:System.Windows.Forms.BindingSource>, 및 <xref:System.Windows.Forms.BindingNavigator> 구성 요소 트레이에 나타납니다. 다음 그림에서는 TableAdapterManager는 Customers 테이블에 Orders 테이블 관계가 있으므로 추가 됩니다. 이러한 변수는 선언 된 모든 자동 생성 코드에서 폼 클래스의 private 멤버. DataGridView를 채우는 자동으로 생성 된 코드는 form_load 이벤트 처리기에 있습니다. 데이터베이스를 업데이트 하려면 데이터를 저장 하는 것에 대 한 코드는 BindingNavigator에 대 한 저장 이벤트 처리기에 있습니다. 이동 하거나 필요에 따라이 코드를 수정할 수 있습니다.  
  
 ![BindingNavigator 사용 하 여 GridView](../data-tools/media/raddata-gridview-with-bindingnavigator.png "raddata BindingNavigator 사용 하 여 GridView")  
  
 각각의 오른쪽 위 모서리에 있는 스마트 태그를 클릭 하 여 DataGridView 및 BindingNavigator의 동작을 사용자 지정할 수 있습니다.  
  
 ![DataGridView 및 바인딩 Navigator 스마트 태그](../data-tools/media/raddata-datagridview-and-binding-navigator-smart-tags.png "raddata DataGridView 및 바인딩 Navigator 스마트 태그")  
  
 컨트롤은 응용 프로그램 필요 없는 경우 내에서 사용할 수는 **데이터 원본** 창 컨트롤을 추가할 수 있습니다. 자세한 내용은 [데이터 소스 창에 사용자 지정 컨트롤을 추가할](../data-tools/add-custom-controls-to-the-data-sources-window.md)합니다.  
  
 항목을 끌 수도 있습니다는 **데이터 원본** 이미 데이터에 컨트롤을 바인딩할 양식의 컨트롤에 창. 이미 데이터에 바인딩되는 컨트롤에 가장 최근에 끌어 항목에 바인딩됩니다. 유효한 놓기 대상 되도록 컨트롤 수 있어야에서 끌어 끌어 온 항목의 기본 데이터 형식을 표시 합니다 **데이터 원본** 창입니다. 예를 들어 유효 하지 않은 데이터 형식이 있는 항목을 끌기 <xref:System.DateTime> 에 <xref:System.Windows.Forms.CheckBox>이므로 <xref:System.Windows.Forms.CheckBox> 날짜를 표시할 수 없습니다.  
  
## <a name="bind-to--data-in-individual-controls"></a>개별 컨트롤에 데이터 바인딩  
 "자세히" 데이터 원본에 바인딩하는 경우 데이터 집합의 각 열은 별도 컨트롤에 바인딩됩니다.  
  
 ![데이터 원본 세부 정보에 바인딩](../data-tools/media/raddata-bind-data-source-to-details.png "raddata 세부 정보를 데이터 원본 바인드")  
  
> [!IMPORTANT]
> 위의 그림에서, Orders 테이블에서가 아니라 고객 테이블의 Orders 속성에서 끌어 옵니다. Customer.Orders 속성에 바인딩하여 탐색 명령은 DataGridView에 대 한 세부 사항 컨트롤이에 즉시 반영 됩니다. Orders 테이블에서 끌어 놓은 경우 컨트롤은 여전히 데이터 집합에 바인딩할 수 있지만 하지 DataGridView를 사용 하 여 이러한 하지 동기화 됩니다.  
  
 다음 그림에 나와 기본 Customers 테이블의 Orders 속성 "Details"에 바인딩된 후 폼에 추가 되는 데이터 바인딩된 컨트롤에는 **데이터 원본** 창입니다.  
  
 ![Orders 테이블 세부 정보에 바인딩된](../data-tools/media/raddata-orders-table-bound-to-details.png "raddata Orders 테이블 바인딩 세부 정보")  
  
 각 컨트롤에 스마트 태그는 또한 note 합니다. 이 태그에만 해당 컨트롤에 적용 되는 사용자 지정 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
