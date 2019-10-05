---
title: Office 솔루션에서 런타임에 바인딩
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62224006d04e0a1e7447053e868dd9946f00c97e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583948"
---
# <a name="late-binding-in-office-solutions"></a>Office 솔루션에서 런타임에 바인딩
  Office 응용 프로그램의 개체 모델에서 일부 형식은 런타임에 바인딩 기능을 통해 사용할 수 있는 기능을 제공 합니다. 예를 들어, 일부 메서드 및 속성은 다양 한 유형의 Office 응용 프로그램의 컨텍스트에 따라 개체를 반환할 수 있으며 다른 메서드나 다른 컨텍스트에서 속성 형식도 노출할 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic 프로젝트 **Option Strict** 해제 되어 Visual C# 대상으로 하는 프로젝트를 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 또는 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 이러한 런타임에 바인딩 기능을 사용 하는 형식으로 직접 사용할 수 있습니다.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>암시적 및 명시적 캐스팅 개체의 반환 값
 다양 한 메서드 및 속성 주 interop 어셈블리 (Pia)를 반환 하는 Microsoft Office에서 <xref:System.Object> 값으로 하므로 여러 다른 유형의 개체를 반환할 수 있습니다. 예를 들어를 <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> 속성에서 반환을 <xref:System.Object> 반환 값 수 있기 때문에 <xref:Microsoft.Office.Interop.Excel.Worksheet> 또는 <xref:Microsoft.Office.Interop.Excel.Chart> 활성 시트에 따라 개체.

 메서드 또는 속성을 반환 하는 경우는 <xref:System.Object>를 명시적으로 변환 해야 (Visual Basic)에서는 개체 Visual Basic 프로젝트에서 올바른 형식으로 위치 **Option Strict** 켜져 합니다. 명시적으로 캐스팅할 필요가 없습니다 <xref:System.Object> Visual Basic 프로젝트에서 값을 반환 합니다. 여기서 **Option Strict** 꺼져 있습니다.

 반환 값의 가능한 형식을 반환 하는 멤버에 대 한 참조 설명서는 대부분의 경우에서 나열 된 <xref:System.Object>합니다. 개체를 캐스팅 또는 변환 코드 편집기에서 개체에 대 한 IntelliSense를 사용할 수 있습니다.

 Visual Basic의 변환에 대 한 자세한 내용은 [암시적 변환과 명시적 변환 &#40;Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) 하 고 [CType function &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).

### <a name="examples"></a>예제
 다음 코드 예제에는 Visual Basic 프로젝트에서 특정 형식으로 개체를 캐스팅 하는 방법을 보여 줍니다. 여기서 **Option Strict** 켜져 있습니다. 이 유형의 프로젝트를 명시적으로 캐스팅 해야 합니다 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> 속성을 <xref:Microsoft.Office.Interop.Excel.Range>입니다. 이 예제에서는 문서 수준 Excel 프로젝트 이라는 워크시트 클래스가 필요 `Sheet1`합니다.

 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]

 다음 코드 예제에는 Visual Basic 프로젝트에서 특정 형식으로 개체를 암시적으로 캐스팅 하는 방법을 보여 줍니다. 여기서 **Option Strict** 는 꺼져 있거나 시각적 개체에 C# 대상으로 하는 프로젝트를 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]합니다. 이러한 유형의 프로젝트에는 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> 속성으로 암시적으로 캐스팅 되는 <xref:Microsoft.Office.Interop.Excel.Range>합니다. 이 예제에서는 문서 수준 Excel 프로젝트 이라는 워크시트 클래스가 필요 `Sheet1`합니다.

 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]

## <a name="access-members-that-are-available-only-through-late-binding"></a>런타임에 바인딩을 통해서만 사용할 수 있는 멤버에 액세스
 일부 속성 및 메서드 Office Pia의 런타임에 바인딩을 통해서만 사용할 수 있습니다. Visual Basic에서 프로젝트 위치 **Option Strict** 꺼져 있거나 시각적 개체에 C# 대상으로 하는 프로젝트를 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 또는 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], 런타임에 바인딩된 멤버에 액세스할 수 이러한 언어의 런타임에 바인딩 기능을 사용할 수 있습니다. Visual Basic에서 프로젝트 위치 **Option Strict** 가 on으로 리플렉션을 사용 하면 이러한 멤버에 액세스를 해야 합니다.

### <a name="examples"></a>예제
 다음 코드 예제에는 Visual Basic 프로젝트에서 런타임에 바인딩된 멤버에 액세스 하는 방법을 보여 줍니다. 여기서 **Option Strict** 는 꺼져 있거나 시각적 개체에 C# 대상으로 하는 프로젝트를 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]합니다. 이 예제에서는 런타임에 바인딩된 액세스 **이름을** 의 속성을 **파일 열기** Word에서 대화 상자. 이 예제를 사용 하려면에서 실행 합니다 `ThisDocument` 또는 `ThisAddIn` Word 프로젝트의 클래스입니다.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 다음 코드 예제에는 리플렉션을 사용 하 여 Visual Basic 프로젝트에서 동일한 작업을 수행 하는 방법을 보여 줍니다. 여기서 **Option Strict** 켜져 있습니다.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>참고자료
- [Office 솔루션에서 코드를 작성 합니다.](../vsto/writing-code-in-office-solutions.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
- [Dynamic 형식 사용 &#40;C&#35; 프로그래밍 가이드&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict 문](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [리플렉션(C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [리플렉션(Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Office 솔루션을 만들고 디자인](../vsto/designing-and-creating-office-solutions.md)
