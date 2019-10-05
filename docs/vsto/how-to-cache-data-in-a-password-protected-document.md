---
title: '방법: 암호로 보호 된 문서의 데이터 캐시'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], protected documents
- datasets [Office development in Visual Studio], caching
- data [Office development in Visual Studio], caching
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c231aac3b78ddb5100cc06600059045fdc463e51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826747"
---
# <a name="how-to-cache-data-in-a-password-protected-document"></a>방법: 암호로 보호 된 문서의 데이터 캐시
  문서 또는 통합 문서를 암호로 보호 되는 데이터 캐시에 데이터를 추가 하는 경우 캐시 된 데이터의 변경 내용은 자동으로 저장 되지 않습니다. 프로젝트의 두 메서드를 재정의 하 여 캐시 된 데이터 변경 내용을 저장할 수 있습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="caching-in-word-documents"></a>Word 문서에서 캐싱

### <a name="to-cache-data-in-a-word-document-that-is-protected-with-a-password"></a>암호로 보호 되는 Word 문서에서 데이터를 캐시 하려면

1. 에 `ThisDocument` 클래스, 공용 필드 또는 속성을 캐시 하도록 표시 합니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)합니다.

2. 재정의 <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> 의 메서드는 `ThisDocument` 클래스 및 문서에서 보호를 제거 합니다.

     문서를 저장 하는 경우는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 문서의 보호를 해제할 수 있도록이 메서드를 호출 합니다. 이 캐시 된 데이터를 저장할 수는 변경할 수 있습니다.

3. 재정의 <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> 의 메서드는 `ThisDocument` 클래스 및 문서 보호를 다시 적용 합니다.

     문서를 저장 한 후의 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 문서 보호를 적용할 수 있는 옵션을 제공 하려면이 메서드를 호출 합니다.

### <a name="example"></a>예제
 다음 코드 예제에는 암호로 보호 되는 Word 문서에서 데이터를 캐시 하는 방법을 보여 줍니다. 코드에서 보호를 제거 하기 전에 합니다 <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> 메서드를 현재 저장 <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> 값을 동일한 형식의 보호에 다시 적용할 수 있도록 합니다 <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> 메서드.

 [!code-csharp[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedDocument/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedDocument/ThisDocument.vb#1)]

### <a name="compile-the-code"></a>코드 컴파일
 이 코드를 추가 합니다 `ThisDocument` 프로젝트의 클래스입니다. 이 코드는 암호 라는 필드에 저장 되어 있다고 가정 `securelyStoredPassword`합니다.

## <a name="cache-in-excel-workbooks"></a>Excel 통합 문서에서 캐시
 Excel 프로젝트에는이 절차가 필요를 사용 하 여 암호를 사용 하 여 전체 통합 문서를 보호 하는 경우에를 <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> 메서드. 이 절차를 사용 하 여 특정 워크시트가 암호로 보호 하는 경우에 필요 없는 <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> 메서드.

### <a name="to-cache-data-in-an-excel-workbook-that-is-protected-with-a-password"></a>암호로 보호 되는 Excel 통합 문서에서 데이터를 캐시

1. 에 `ThisWorkbook` 클래스 또는 중 하나는 `Sheet` *n* public 필드나 속성을 캐시 하도록 클래스를 표시 합니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)합니다.

2. 재정의 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> 의 메서드는 `ThisWorkbook` 클래스 및 통합 문서에서 보호를 제거 합니다.

     통합 문서를 저장할 때는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 를 통합 문서를 해제할 수 있는 기회를 제공 하려면이 메서드를 호출 합니다. 이 캐시 된 데이터를 저장할 수는 변경할 수 있습니다.

3. 재정의 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> 의 메서드는 `ThisWorkbook` 클래스 및 문서 보호를 다시 적용 합니다.

     통합 문서 저장 되 면는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 통합 문서에 대 한 보호를 적용할 수 있는 옵션을 제공 하려면이 메서드를 호출 합니다.

### <a name="example"></a>예제
 다음 코드 예제에는 암호로 보호 되는 Excel 통합 문서에서 데이터를 캐시 하는 방법을 보여 줍니다. 코드에서 보호를 제거 하기 전에 합니다 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> 메서드를 현재 저장 <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> 및 <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> 값을 동일한 형식의 보호에 다시 적용할 수 있도록는 <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> 메서드.

 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/VisualBasic/Trin_CachedDataProtectedWorkbook/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../vsto/codesnippet/CSharp/Trin_CachedDataProtectedWorkbook/ThisWorkbook.cs#1)]

### <a name="compile-the-code"></a>코드 컴파일
 이 코드를 추가 합니다 `ThisWorkbook` 프로젝트의 클래스입니다. 이 코드는 암호 라는 필드에 저장 되어 있다고 가정 `securelyStoredPassword`합니다.

## <a name="see-also"></a>참고자료
- [데이터 캐시](../vsto/caching-data.md)
- [방법: 오프 라인 이나 서버에서 사용 하기 위해 데이터 캐시](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)
- [방법: Office 문서에서 데이터 원본을 프로그래밍 방식으로 캐시](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
