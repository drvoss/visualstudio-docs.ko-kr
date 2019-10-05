---
title: XMLNode 컨트롤
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNode control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a8bd5c4612b59f909ae623eb4092a209798f98c5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975729"
---
# <a name="xmlnode-control"></a>XMLNode 컨트롤
  **중요 한** Microsoft Word에 대 한이 항목의 설정 정보가 혜택 및 개인 및 United States 및 해당 지역 외부에 위치한는 또는 사용 하는 조직의 사용에 단독으로 표시 되었거나 개발 실행 되는 프로그램, Microsoft Word 2010 년 1 월, Microsoft 구현의 특정 기능을 제거 하는 경우 하기 전에 Microsoft에서 사용이 허가 된 제품에서에서 관련 된 사용자 지정 XML Microsoft Word입니다. Microsoft Word에 대 한이 정보를 읽거나 개인 이나 조직에서는 미국에 있는 Microsoft Word 2010 년 1 월 10 일 후 Microsoft에서 사용이 허가 된 제품에서 실행 되는 프로그램을 개발 하거나를 사용 하는 해당 지역에서 사용 될 수 있습니다. ; 이러한 제품 구매 및 미국 이외의 용도로 사용이 허가 된 날짜 이전에 사용이 허가 된 제품으로 동일한 작동 하지 않습니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNode> 컨트롤은 이벤트를 노출 하 고 데이터에 바인딩될 수 있는 매핑된 XML 노드 개체입니다. <xref:Microsoft.Office.Tools.Word.XMLNode> 컨트롤이-반복 되지 않는 스키마 요소를 Microsoft Office Word 문서에 매핑될 경우에 만들어집니다. Visual Studio에서 XML 노드를 만든 후 Word 개체 모델을 트래버스 하지 않고 직접 프로그래밍할 수 있습니다.

 <xref:Microsoft.Office.Tools.Word.XMLNode> 만 Word에서 요소 매핑을 제거 하 여 컨트롤을 삭제할 수 있습니다.

## <a name="bind-data-to-the-control"></a>컨트롤에 데이터 바인딩
 <xref:Microsoft.Office.Tools.Word.XMLNode> 컨트롤은 단순 데이터 바인딩을 지원 합니다. XML 노드를 사용 하 여 데이터 원본에 바인딩할 수 해야는 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> 속성입니다. 바인딩된 데이터 세트의 데이터가 업데이트되면 <xref:Microsoft.Office.Tools.Word.XMLNode> 컨트롤이 변경 내용을 반영합니다.

## <a name="formatting"></a>서식
 에 적용할 수 있는 형식 지정에 <xref:Microsoft.Office.Interop.Word.XMLNode> 개체에 적용할 수 있습니다는 <xref:Microsoft.Office.Tools.Word.XMLNode> 컨트롤입니다. 글꼴, 밑줄 스타일 및 스타일 문자 포함 됩니다.

## <a name="events"></a>이벤트
 <xref:Microsoft.Office.Tools.Word.XMLNode> 컨트롤에 대해 다음 이벤트를 사용할 수 있습니다.

- <xref:Microsoft.Office.Tools.Word.XMLNode.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNode.BindingContextChanged>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNode.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNode.ValidationError>

## <a name="compare-events"></a>이벤트를 비교 합니다.
 특정 컨텍스트 내에서 커서를 이동할 때 이벤트를 캡처할 수 <xref:Microsoft.Office.Tools.Word.XMLNode> 제어 합니다. 예를 들어 있을 수 있습니다는 <xref:Microsoft.Office.Tools.Word.XMLNode> 라는 컨트롤 `Customer` 자식이 있는 <xref:Microsoft.Office.Tools.Word.XMLNode> 이라는 컨트롤이 `Company`, 및 `Company` 에 두 명의 자식 <xref:Microsoft.Office.Tools.Word.XMLNode> 라는 컨트롤 `CompanyName` 및 `CompanyRegion` 같이:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 작업 창에서 컨트롤을 표시 하려는 경우 때마다 커서가 이동에 `Company` 노드는 중요 하지 않습니다 커서에 배치할지 여부를 `CompanyName` 또는 `CompanyRegion` 컨텍스트 내에서 모두 되므로 `Company`합니다. 이 경우 코드를 작성할 수 있습니다 합니다 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 이벤트를 `Company`입니다.

 대부분의 경우, 커서가 <xref:Microsoft.Office.Tools.Word.XMLNode> 컨트롤을 모두 합니다 <xref:Microsoft.Office.Tools.Word.XMLNode.Select> 및 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 이벤트가 발생 합니다. 다음 표에서 이러한 이벤트 간의 차이점을 보여 줍니다.

|이벤트 선택|ContextEnter 이벤트|
|------------------|------------------------|
|커서에 배치 된 경우에 발생 한 <xref:Microsoft.Office.Tools.Word.XMLNode>합니다.|커서에 배치 된 경우 발생을 <xref:Microsoft.Office.Tools.Word.XMLNode> 또는 노드의 컨텍스트 바깥쪽 영역에서 하위 노드 중 하나입니다. 즉, 컨텍스트를 변경 하는 경우에이 발생 합니다.|

 외부에서 커서를 이동할 때 예를 들어 `Customer` 에 `CompanyName`의 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 이벤트에 대 한 `Customer`를 `Company`, 및 `CompanyName` 발생 합니다. 다음 커서를 이동 하는 경우 `CompanyName` 하 `CompanyRegion`만 합니다 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextEnter> 이벤트에 대 한 `CompanyRegion` 둘 다의 컨텍스트 내에서 여전히 때문에 발생 `Company` 및 `Customer`.

 경우에 동일한 차이점이 합니다 <xref:Microsoft.Office.Tools.Word.XMLNode.ContextLeave> 이벤트 및 <xref:Microsoft.Office.Tools.Word.XMLNode.Deselect> 이벤트입니다.

## <a name="see-also"></a>참고자료
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [확장 된 개체를 사용 하 여 Word 자동화](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNodes 컨트롤](../vsto/xmlnodes-control.md)
- [방법: Word 문서에 XMLNode 컨트롤 추가](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)
- [방법: Visual Studio 내부의 Word 문서에 스키마 매핑](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍 방식으로 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
