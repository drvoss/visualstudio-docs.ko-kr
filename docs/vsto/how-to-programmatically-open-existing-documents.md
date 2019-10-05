---
title: '방법: 프로그래밍 방식으로 기존 문서 열기'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 490dda6e5357cd0933c6a8b494cc4373038e5c1c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812399"
---
# <a name="how-to-programmatically-open-existing-documents"></a>방법: 프로그래밍 방식으로 기존 문서 열기
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> 정규화 된 경로 및 파일 이름으로 지정 된 기존 Microsoft Office Word 문서를 엽니다. 이 메서드는 반환 된 <xref:Microsoft.Office.Interop.Word.Document> 열린된 문서를 나타내는입니다.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>문서를 열려면

- 호출을 <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> 메서드는 <xref:Microsoft.Office.Interop.Word.Documents> 컬렉션 및 문서에 대 한 경로 제공 합니다.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>읽기 전용으로 문서를 열려면

- 호출을 <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> 메서드를 문서에 대 한 경로 입력 하 고 설정 합니다 *ReadOnly* 인수를 **True** 메서드 호출의.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>코드 컴파일
 이 코드 예제에는 다음이 필요합니다.

- 라는 문서가 *NewDocument.doc* 라는 디렉터리에 있어야 *테스트* 에서 C 드라이브입니다.

## <a name="see-also"></a>참고자료
- [방법: 프로그래밍 방식으로 새 문서 만들기](../vsto/how-to-programmatically-create-new-documents.md)
- [방법: 프로그래밍 방식으로 문서 닫기](../vsto/how-to-programmatically-close-documents.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
