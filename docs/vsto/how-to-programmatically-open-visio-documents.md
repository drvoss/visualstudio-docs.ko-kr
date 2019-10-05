---
title: '방법: 프로그래밍 방식으로 Visio 문서 열기'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b863040bcceb4e86aae7ed4efd83c2466eec12c6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812253"
---
# <a name="how-to-programmatically-open-visio-documents"></a>방법: 프로그래밍 방식으로 Visio 문서 열기
  기존 Microsoft Office Visio 문서를 여는 방법은 두 가지가 있습니다. 열기 및 OpenEx 합니다. OpenEx 메서드는 인수는 호출자에 게 문서가 열리는 방식을 지정할 수 있다는 점을 제외 하 고 Open 메서드가 동일 합니다.

 개체 모델에 대한 자세한 내용은 VBA 참조 설명서에서 [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) 메서드 및 [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) 메서드를 참조하세요.

## <a name="open-a-visio-document"></a>Visio 문서 열기

### <a name="to-open-a-visio-document"></a>Visio 문서를 열려면

- `Microsoft.Office.Interop.Visio.Documents.Open` 메서드를 호출하고 Visio 문서의 정규화된 경로를 제공합니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>지정 된 인수를 사용 하 여 Visio 문서 열기

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Visio 문서를 읽기 전용 및 도킹하여 열려면

- `Microsoft.Office.Interop.Visio.Documents.OpenEx` 메서드를 호출하여 Visio 문서의 정규화된 경로를 제공하고 사용하려는 인수(이 경우, 도킹됨 및 읽기 전용)를 포함합니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>코드 컴파일
 이 코드 예제에는 다음이 필요합니다.

- 명명 된 Visio 문서 `myDrawing.vsd` 라는 디렉터리에 있어야 합니다 `Test` 에 *My Documents* 폴더 (Windows XP 및 이전) 또는 *문서* 폴더 (Windows Vista).

## <a name="see-also"></a>참고자료
- [Visio 솔루션](../vsto/visio-solutions.md)
- [Visio 개체 모델 개요](../vsto/visio-object-model-overview.md)
- [방법: 프로그래밍 방식으로 새 Visio 문서 만들기](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 닫기](../vsto/how-to-programmatically-close-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 저장](../vsto/how-to-programmatically-save-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 인쇄](../vsto/how-to-programmatically-print-visio-documents.md)
