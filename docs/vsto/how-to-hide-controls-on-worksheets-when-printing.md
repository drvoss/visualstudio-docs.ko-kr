---
title: '방법: 인쇄할 때 워크시트에서 컨트롤 숨기기'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- printing [Office development in Visual Studio], worksheets
- controls [Office development in Visual Studio], hiding while printing
- printing [Office development in Visual Studio], hiding controls
- worksheets, hiding controls when printing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bb7ee0a937e6cb901704763e1f4ead478d99e0e8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419439"
---
# <a name="how-to-hide-controls-on-worksheets-when-printing"></a>방법: 인쇄할 때 워크시트에서 컨트롤 숨기기
  Windows Forms 컨트롤을 포함 하는 Microsoft Office Excel 문서를 인쇄할 때 컨트롤 인쇄 된 워크시트에 표시 됩니다. 워크시트를 인쇄할 때 컨트롤을 숨길 수 있습니다.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

> [!NOTE]
> 와 같은 데이터를 표시 하는 컨트롤을 숨기면는 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>, 컨트롤의 데이터 인쇄 된 워크시트에 표시 되지 것입니다.

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="to-hide-controls-when-a-worksheet-is-printed"></a>인쇄할 때 워크시트의 컨트롤을 숨기

1. 또는 Visual Studio에서 Excel 프로젝트를 열고 만들고 확인 하는 **Sheet1** 디자이너에 표시 됩니다. 프로젝트를 만드는 방법에 대 한 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)합니다.

2. **공용 컨트롤** 탭의 **도구 상자**를 끌어를 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 셀에 대 한 control 권한 `Sheet1`.

3. 에 **속성** 창에서 설정 합니다 <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> 속성을 **False**합니다.

## <a name="see-also"></a>참고자료
- [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)
- [Windows Forms 컨트롤에 대 한 Office 문서 개요](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [방법: Office 문서에 Windows Forms 컨트롤 추가](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [방법: 워크시트 셀에서 컨트롤 크기 조정](../vsto/how-to-resize-controls-within-worksheet-cells.md)
