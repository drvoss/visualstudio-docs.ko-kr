---
title: '방법: 데이터베이스의 데이터로 워크시트 채우기'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 67c12843d00bf8d5af51fa7af3175077527afa58
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967763"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>방법: 데이터베이스의 데이터로 워크시트 채우기

Windows Forms 프로젝트에서 데이터를 액세스 하는 동일한 방식으로 문서 수준 Office 프로젝트의 데이터를 액세스할 수 있습니다. 동일한 도구 및 코드를 사용하여 데이터를 솔루션으로 가져오며, Windows Forms 컨트롤을 사용하여 데이터를 표시할 수도 있습니다. 또한 이벤트 및 데이터 바인딩 기능을 사용 하 여 향상 된 Microsoft Office Excel에서 네이티브 개체인 호스트 컨트롤 이라는 컨트롤 활용을 걸릴 수 있습니다. 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)합니다.

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

다음 예제에서는 디자이너를 사용하여 문서 수준 프로젝트에 데이터 바인딩된 컨트롤을 추가하는 방법을 보여 줍니다. 런타임 시 응용 프로그램 수준 프로젝트에서 데이터 바인딩된 컨트롤을 추가 하는 방법의 예제를 참조 하세요. [연습: VSTO 추가 기능 프로젝트의 복합 데이터 바인딩](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)합니다.

![비디오 링크](../vsto/media/playvideo.gif "비디오 링크") 관련된 비디오 데모를 참조 하세요. [어떻게 할까요? Excel 워크시트에 데이터를 전송? ](http://go.microsoft.com/fwlink/?LinkID=130277), 및 [어떻게 할까요? : Excel에서 데이터베이스 데이터 사용? ](http://go.microsoft.com/fwlink/?LinkID=130287).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>디자인 타임에 데이터 바인딩된 컨트롤을 워크시트에 추가

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>데이터베이스의 데이터로 워크시트를 채우려면

1. 디자이너에서 워크시트를 열고 Visual Studio에서 Excel 문서 수준 프로젝트를 엽니다.

2. **데이터 원본** 창을 열고 데이터베이스에서 데이터 원본을 만듭니다. 자세한 내용은 [새 연결 추가](../data-tools/add-new-connections.md)합니다.

3. 테이블에서 마우스를 끌어서 합니다 **데이터 원본** 워크시트 창.

다음 컨트롤 중 하나는 워크시트에 만들어집니다.

- 필드를 끌면는 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 워크시트에 만들어집니다. 자세한 내용은 [NamedRange 컨트롤](../vsto/namedrange-control.md)합니다.

- 테이블을 끌면는 <xref:Microsoft.Office.Tools.Excel.ListObject> 컨트롤이 워크시트에 만들어집니다. 자세한 내용은 [ListObject 컨트롤](../vsto/listobject-control.md)합니다.

테이블을 선택 하 여 다른 컨트롤을 추가 하거나 필드에 **데이터 원본** 창과 드롭 다운 목록에서 다른 컨트롤을 선택 합니다.

## <a name="objects-in-the-project"></a>프로젝트의 개체

컨트롤 외에도 다음과 같은 데이터 관련 개체가 프로젝트에 자동으로 추가됩니다.

- 데이터베이스에서 연결된 데이터 테이블을 캡슐화하는 형식화된 데이터 세트. 자세한 내용은 [Visual Studio에서 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)합니다.

- 컨트롤을 형식화된 데이터 세트에 연결하는 <xref:System.Windows.Forms.BindingSource>. 자세한 내용은 [BindingSource 구성 요소 개요](/dotnet/framework/winforms/controls/bindingsource-component-overview)합니다.

- 데이터베이스에 형식화 된 데이터 집합을 연결 하는 TableAdapter. 자세한 내용은 [TableAdapter 개요](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)합니다.

- TableAdapterManager를 계층적 업데이트를 사용 하도록 설정 하려면 데이터 집합의 테이블 어댑터를 조정 하는 데 사용 되는 합니다. 자세한 내용은 [계층적 업데이트](../data-tools/hierarchical-update.md) 하 고 [TableAdapterManager 참조](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)합니다.

프로젝트를 실행하면 컨트롤이 데이터 소스의 첫 번째 레코드를 표시합니다. <xref:System.Windows.Forms.BindingSource>를 사용하여 사용자가 레코드를 스크롤할 수 있게 할 수 있습니다.

### <a name="to-scroll-through-the-records"></a>레코드를 스크롤하려면

- <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 및 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>와 같은 <xref:System.Windows.Forms.BindingSource> 메서드를 사용합니다.

형식화 된 데이터 집합 및 데이터베이스에 업데이트를 보내는 방법에 대 한 정보를 참조 하세요. [방법: 호스트 컨트롤의 데이터로 데이터 소스를 업데이트](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)합니다.

## <a name="see-also"></a>참고자료

- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [새 데이터 소스 추가](../data-tools/add-new-data-sources.md)
- [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [방법: 개체의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [방법: 데이터베이스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [방법: 서비스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-services.md)
- [방법: 호스트 컨트롤의 데이터로 데이터 소스를 업데이트 합니다.](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [어떻게 할까요 Excel 워크시트에 데이터를 전송 합니다.](http://go.microsoft.com/fwlink/?LinkID=130277)
- [어떻게 할까요 : Excel에서 데이터베이스 데이터 사용?](http://go.microsoft.com/fwlink/?LinkID=130287)