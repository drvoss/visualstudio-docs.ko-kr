---
title: '방법: 프로그래밍 방식으로 Visio 문서 닫기'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 474efcb62cf7cadd9de82e41ff2ad36cebc046cb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575366"
---
# <a name="how-to-programmatically-close-visio-documents"></a>방법: 프로그래밍 방식으로 Visio 문서 닫기
  `Microsoft.Office.Interop.Visio.Document.Close` 메서드를 사용하여 활성 Microsoft Office Visio 문서를 닫을 수 있습니다.

 이 메서드에 대한 자세한 내용은 VBA 참조 설명서에서 [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) 메서드를 참조하세요.

## <a name="close-the-active-document"></a>활성 문서 닫기

### <a name="to-close-the-active-document"></a>활성 문서를 닫으려면

- `Microsoft.Office.Interop.Visio.Document.Close` 메서드를 호출하여 활성 문서를 닫습니다.

     다음 코드 예제를 사용 하려면 실행을 `ThisAddIn` Visio 용 VSTO 추가 기능에 프로젝트의 클래스입니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>참고자료
- [Visio 솔루션](../vsto/visio-solutions.md)
- [Visio 개체 모델 개요](../vsto/visio-object-model-overview.md)
- [방법: 프로그래밍 방식으로 새 Visio 문서 만들기](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 열기](../vsto/how-to-programmatically-open-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 저장](../vsto/how-to-programmatically-save-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 인쇄](../vsto/how-to-programmatically-print-visio-documents.md)
