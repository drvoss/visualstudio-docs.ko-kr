---
title: XMLNodes 컨트롤
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XMLNodes control, events
- XMLNodes control
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9ad16165924a33a25dab2b1cfb49a0a7bbfe0875
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63421530"
---
# <a name="xmlnodes-control"></a>XMLNodes 컨트롤
  **중요 한** Microsoft Word에 대 한이 항목의 설정 정보가 혜택 및 개인 및 United States 및 해당 지역 외부에 위치한는 또는 사용 하는 조직의 사용에 단독으로 표시 되었거나 개발 실행 되는 프로그램, Microsoft Word 2010 년 1 월, Microsoft 구현의 특정 기능을 제거 하는 경우 하기 전에 Microsoft에서 사용이 허가 된 제품에서에서 관련 된 사용자 지정 XML Microsoft Word입니다. Microsoft Word에 대 한이 정보를 읽거나 개인 이나 조직에서는 미국에 있는 Microsoft Word 2010 년 1 월 10 일 후 Microsoft에서 사용이 허가 된 제품에서 실행 되는 프로그램을 개발 하거나를 사용 하는 해당 지역에서 사용 될 수 있습니다. ; 이러한 제품 구매 및 미국 이외의 용도로 사용이 허가 된 날짜 이전에 사용이 허가 된 제품으로 동일한 작동 하지 않습니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤은 이벤트를 노출 하는 매핑된 XML 노드 개체의 컬렉션입니다. <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤이 반복 스키마 요소를 Microsoft Office Word 문서에 매핑될 경우에 만들어집니다. 반복 되는 요소에 자식 요소가 있으면 각 자식 요소의 생성 됩니다는 <xref:Microsoft.Office.Tools.Word.XMLNodes> 제어 합니다.

 Visual Studio의 XML 노드 컬렉션을 만든 후 Word 개체 모델을 트래버스 하지 않고 직접 컨트롤에 대해 프로그래밍할 수 있습니다. <xref:Microsoft.Office.Tools.Word.XMLNodes> 만 문서에서 요소 매핑을 제거 하 여 컨트롤을 삭제할 수 있습니다.

> [!NOTE]
> 자식 요소를 액세스 하는 경우는 <xref:Microsoft.Office.Tools.Word.XMLNodes> 를 통해 제어할 합니다 <xref:Microsoft.Office.Tools.Word.XMLNodes.Item%2A> 속성을 반환을 <xref:Microsoft.Office.Interop.Word.XMLNode> 개체 대신 <xref:Microsoft.Office.Tools.Word.XMLNode> 컨트롤. 자세한 내용은 [호스트 항목 및 호스트 컨트롤의 프로그래밍 방식으로 제한](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)합니다.

## <a name="bind-data-to-the-control"></a>컨트롤에 데이터 바인딩
 <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤 데이터 바인딩을 지원 하지 않습니다. 왜냐하면는 <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤에 복잡 한 데이터 바인딩 기능이 없는 및 단순 데이터 바인딩 나타낼 수 없는 반복 되는 데이터입니다.

## <a name="formatting"></a>서식
 문서 내 텍스트에 적용할 수 있는 모든 형식에 적용할 수 있습니다는 <xref:Microsoft.Office.Tools.Word.XMLNodes> 제어 합니다.

## <a name="events"></a>이벤트
 에 사용할 수 있는 이벤트는 <xref:Microsoft.Office.Tools.Word.XMLNodes> 제어 됩니다.

- <xref:Microsoft.Office.Tools.Word.XMLNodes.AfterInsert>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.BeforeDelete>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect>

- <xref:System.ComponentModel.IComponent.Disposed>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.Select>

- <xref:Microsoft.Office.Tools.Word.XMLNodes.ValidationError>

## <a name="compare-events"></a>이벤트를 비교 합니다.
 특정 컨텍스트 내에서 커서를 이동할 때 이벤트를 캡처할 수 <xref:Microsoft.Office.Tools.Word.XMLNodes> 제어 합니다. 예를 들어 있을 수 있습니다는 <xref:Microsoft.Office.Tools.Word.XMLNodes> 라는 컨트롤 `Customer` 자식이 있는 <xref:Microsoft.Office.Tools.Word.XMLNodes> 이라는 컨트롤이 `Company`, 및 `Company` 에 두 명의 자식 <xref:Microsoft.Office.Tools.Word.XMLNodes> 라는 컨트롤 `CompanyName` 및 `CompanyRegion` 같이:

```xml
<Customer>
    <Company>
        <CompanyName>
        <CompanyRegion>
```

 작업 창에서 컨트롤을 표시 하려는 경우 때마다 커서가 이동에 `Company` 노드는 중요 하지 않습니다 커서에 배치할지 여부를 `CompanyName` 또는 `CompanyRegion` 컨텍스트 내에서 모두 되므로 `Company`합니다. 이 경우 코드를 작성할 수 있습니다 합니다 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 이벤트를 `Company`입니다.

 대부분의 경우, 커서가 <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤을 모두 합니다 <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> 및 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 이벤트가 발생 합니다. 다음 표에서 이러한 이벤트 간의 차이점을 보여줍니다.

|이벤트 선택|ContextEnter 이벤트|
|------------------|------------------------|
|커서의 노드 중 하나에 배치 된 경우 발생 합니다 <xref:Microsoft.Office.Tools.Word.XMLNodes> 컬렉션입니다.|커서 노드 또는 하위 노드 중 하나에 배치 된 경우 발생 합니다 <xref:Microsoft.Office.Tools.Word.XMLNodes> 노드의 컨텍스트 바깥쪽 영역에서 수집 합니다. 컨텍스트 변경 하는 경우에 발생 즉, 여러 중첩 발생할 수 있습니다 및 <xref:Microsoft.Office.Tools.Word.XMLNodes> 컨트롤입니다.|

 외부에서 커서를 이동할 때 예를 들어 `Customer` 에 `CompanyName`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 에 대 한 이벤트 `Customer`, `Company`, 및 `CompanyName` 발생 합니다. 커서를 옮기면 `CompanyName` 에 `CompanyRegion`, <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextEnter> 이벤트에 대해서만 `CompanyRegion` 컨텍스트 둘 다에 대해 동일 하기 때문에 발생 `Company` 및 `Customer`합니다. 여러 개 있을 수 있습니다 `Company` 문서에서 노드. 커서를 이동 하는 경우는 `CompanyName` 노드로 `Company` 에 `CompanyName` 다른 노드의 `Company`는 동일 하므로 컨텍스트는는 <xref:Microsoft.Office.Tools.Word.XMLNodes.Select> 이벤트가 발생 합니다.

 경우에 동일한 차이점이 합니다 <xref:Microsoft.Office.Tools.Word.XMLNodes.ContextLeave> 이벤트 및 <xref:Microsoft.Office.Tools.Word.XMLNodes.Deselect> 이벤트입니다.

## <a name="see-also"></a>참고자료
- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)
- [확장 된 개체를 사용 하 여 Word 자동화](../vsto/automating-word-by-using-extended-objects.md)
- [XMLNode 컨트롤](../vsto/xmlnode-control.md)
- [방법: Word 문서에 XMLNodes 컨트롤 추가](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)
- [방법: Visual Studio 내부의 Word 문서에 스키마 매핑](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍 방식으로 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
