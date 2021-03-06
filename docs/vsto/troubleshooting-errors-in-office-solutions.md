---
title: Office 솔루션의 오류 문제 해결
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.DesignerDisabled
- VST.Designer.CannotActivate
- VST.Project.ExcelBusy
- VST.SelectDocWizard.AlreadyCustomized
- VST.SelectDocWizard.DocPath
- VST.Project.CannotOpen
- VST.Designer.ErrorsOccurred
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bcc5600f38e2d53244d972e4c4c7094182bfa48c
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672953"
---
# <a name="troubleshoot-errors-in-office-solutions"></a>Office 솔루션의 오류 문제 해결
  Visual Studio에서 Office 솔루션을 개발하는 동안 다음 작업을 수행할 때 문제가 발생할 수 있습니다.  
  
-   [만들기, 업그레이드 및 프로젝트 열기](#creating)  
  
-   [디자이너를 사용 합니다.](#designers)  
  
-   [코드 작성](#code)  
  
-   [프로젝트 빌드](#building)  
  
-   [프로젝트 디버그](#debugging)  
  
##  <a name="creating"></a> 만들기, 업그레이드 및 프로젝트 열기  
 Office 프로젝트를 만들거나 열 때 다음과 같은 오류가 발생할 수 있습니다.  
  
### <a name="the-project-cannot-be-created"></a>프로젝트를 만들 수 없습니다.  
 Office 프로젝트를 만들거나 열려고 할 때 오류가 발생했지만 Visual Studio에 원인을 확인하기에 충분한 정보가 없습니다. 프로젝트를 닫고 Visual Studio를 종료한 후 다시 시작합니다.  
  
 문서 수준 프로젝트를 만들려는 경우 새 프로젝트의 문서와 동일한 이름을 가진 다른 문서가 Excel 또는 Word에서 이미 열려 있을 수 있습니다. Excel 또는 Word의 다른 모든 인스턴스가 닫혀 있는지 확인합니다.  
  
### <a name="control-properties-are-lost-when-you-create-a-new-project-based-on-a-document-from-an-existing-project"></a>기존 프로젝트에서 문서를 기반으로 새 프로젝트를 만들 때 컨트롤 속성이 손실 됩니다.  
 기존 프로젝트의 문서를 기반으로 하여 새 Office 프로젝트를 만드는 경우 문서에 있는 컨트롤의 속성은 새 프로젝트로 복사되지 않습니다. 기존 컨트롤의 속성을 수동으로 다시 설정해야 합니다. 또는 새 프로젝트를 만드는 대신 기존 프로젝트의 복사본을 만들거나 디자이너에서 기존 프로젝트를 새 솔루션에 로드하고 기존 문서에서 새 문서로 컨트롤을 복사하여 붙여넣으면 컨트롤 속성을 유지할 수 있습니다.  
  
### <a name="errors-when-you-create-an-excel-workbook-project-based-on-an-existing-workbook"></a>기존 통합 문서에 따라 Excel 통합 문서 프로젝트를 만드는 경우 오류 발생  
 기존 통합 문서를 기반으로 새 Excel 통합 문서 프로젝트를 만든 경우 다음 오류가 조합을 볼 수 있습니다.  
  
 Excel에서: "개인 정보 경고: 이 문서에는 매크로, ActiveX 컨트롤, XML 확장 팩 정보, 웹 구성 요소가 있습니다. 문서 검사에서 제거할 수 없는 개인 정보가 포함되어 있을 수 있습니다."  
  
 Visual Studio에서: "디자이너를 제대로 로드하지 못했습니다.  
  
 이러한 오류는 해당 개인 정보가 문서 검사를 사용하여 제거된 통합 문서를 기반으로 하는 프로젝트를 만들려는 경우에 발생할 수 있습니다. 이 오류를 방지하려면 프로젝트를 만들기 전에 다음 단계를 수행합니다.  
  
1.  Excel에서 통합 문서를 엽니다.  
  
2.  Excel에서 보안 센터를 엽니다.  
  
3.  에 **개인 정보 옵션** 탭의 선택을 취소 합니다 **저장 시 파일 속성에서 개인 정보 제거** 확인란 합니다.  
  
4.  통합 문서를 저장하고 Excel을 닫습니다.  
  
### <a name="cannot-open-a-project-after-migration"></a>마이그레이션 후 프로젝트를 열 수 없습니다.  
 Office 솔루션이 Microsoft Office 2010으로 마이그레이션된 후 2007 Microsoft Office System만 설치된 개발 컴퓨터에서는 프로젝트를 열 수 없습니다. 다음과 같은 오류가 표시될 수 있습니다.  
  
 "솔루션의 프로젝트 중 하나 이상이 제대로 로드되지 않았습니다. 자세한 내용은 출력 창을 참조하세요."  
  
 "이 프로젝트 형식과 연결된 응용 프로그램이 이 컴퓨터에 설치되어 있지 않아 프로젝트를 만들 수 없습니다. 이 프로젝트 형식과 연결된 Microsoft Office 응용 프로그램을 설치해야 합니다."  
  
 이 문제를 해결 하려면 편집 합니다 *.vbproj* 하거나 *.csproj* 파일입니다. Word 프로젝트의 경우 HostPackage="{763FDC83-64E5-4651-AC9B-28C4FEB985A1}"을 HostPackage="{6CE98B71-D55A-4305-87A8-0D6E368D9600}"으로 바꿉니다. Excel 프로젝트의 경우 HostPackage="{B284B16A-C42C-4438-BDCD-B72F4AC43CFB}"를 HostPackage="{825100CF-0BA7-47EA-A084-DCF3308DAF74}"로 바꿉니다. Outlook 프로젝트의 경우 HostPackage="{D2B20FF5-A6E5-47E1-90E8-463C6860CB05}"를 HostPackage="{20A848B8-E01F-4801-962E-25DB0FF57389}"로 바꿉니다.  
  
 또는 Microsoft Office 2010이 이미 설치된 개발 컴퓨터에서만 마이그레이션된 프로젝트를 열어야 합니다.  
  
### <a name="errors-in-upgraded-office-2003-document-level-projects-that-contain-windows-forms-controls"></a>Windows Forms 컨트롤을 포함 하는 업그레이드 된 Office 2003 문서 수준 프로젝트의 오류  
 Microsoft Office 2003 문서 수준 프로젝트를 업그레이드할 Windows Forms 컨트롤을 포함 하는 문서를 업그레이드 된 프로젝트의 컴파일 또는 런타임 오류가 있을 수 있습니다. 이 문제를 방지하려면 프로젝트를 업그레이드하기 전에 개발 컴퓨터에 Visual Studio 2005 Tools for Office Second Edition Runtime을 설치합니다. 이 런타임 버전은 Microsoft 다운로드 센터의 [Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime(VSTO 2005 SE)(x86)](http://go.microsoft.com/fwlink/?linkid=49612)에서 재배포 가능 패키지로 다운로드할 수 있습니다.  
  
 프로젝트 업그레이드를 완료한 후 다른 Office 솔루션에서 사용되고 있지 않으면 개발 컴퓨터에서 Visual Studio 2005 Tools for Office Second Edition Runtime을 제거할 수 있습니다.  
  
##  <a name="designers"></a> 디자이너를 사용 합니다.  
 문서 수준 프로젝트에서 문서, 통합 문서 또는 워크시트 디자이너를 사용하는 경우 다음과 같은 오류가 발생할 수 있습니다.  
  
### <a name="designer-failed-to-load-correctly"></a>디자이너를 제대로 로드 하지 못했습니다.  
 다음과 같은 경우 Visual Studio에서 디자이너를 열 수 없습니다.  
  
-   Excel 또는 Word가 이미 열려 있고 모달 대화 상자를 표시합니다. 디자이너를 열려면 Excel 또는 Word에서 모달 대화 상자가 열려 있는지 확인하고 열려 있는 모달 대화 상자를 모두 닫습니다. 열려 있는 모달 대화 상자가 없는 경우 Excel 또는 Word에서 응답하기 전에 다른 작업이 필요할 수 있습니다.  
  
-   현재 프로젝트를 디버그 중입니다. 디자이너를 열려면 디버깅을 중지하거나 완료합니다.  
  
-   Excel을 시작할 때 개발 컴퓨터에 설치된 Excel VSTO 추가 기능에서 대화 상자를 표시합니다. Excel 문서 수준 프로젝트를 만들려면 먼저 VSTO 추가 기능을 사용하지 않도록 설정해야 합니다.  
  
### <a name="controls-appear-as-black-rectangles-on-the-document-or-worksheet"></a>컨트롤이 문서 또는 워크시트에서 검은색 사각형으로 표시  
 문서 또는 워크시트에서 컨트롤을 그룹화하는 경우 Visual Studio에서 더 이상 해당 컨트롤을 인식하지 않습니다. 그룹화 된 컨트롤에 액세스할 수 합니다 **속성** 창 고, 문서 또는 워크시트에서 검은색 사각형으로 표시 합니다. 해당 기능을 복원하려면 컨트롤 그룹을 해제해야 합니다.  
  
### <a name="controls-on-a-word-template-are-not-visible-in-visual-studio"></a>컨트롤을 Word 서식 파일에서 Visual Studio에 표시 되지 않습니다.  
 Visual Studio 디자이너에서 Word 서식 파일을 여는 경우 텍스트와 인라인이 아닌 서식 파일의 컨트롤이 표시되지 않을 수 있습니다. Visual Studio에서 Word 서식 파일을 열기 때문에 이것이 **Normal** 보기. 컨트롤을 보려면 클릭 합니다 **뷰** 메뉴에서 **Microsoft Office Word 보기** 을 클릭 한 다음 **인쇄 레이아웃**합니다.  
  
### <a name="insert-clip-art-command-does-nothing-in-the-visual-studio-designer"></a>클립 아트 삽입 명령을 Visual Studio 디자이너에 아무 작업도 수행 하지  
 Excel 또는 Word Visual Studio 디자이너에에서 열려 있는 경우 클릭 하는 **클립 아트** 단추를 **그림** 리본의 열리지는 **클립 아트** 작업창입니다. 클립 아트를 추가 하려면 통합 문서 또는 주 프로젝트 폴더에 있는 문서 복사본을 열어야 합니다 (에 있는 복사본 아님 합니다 *\bin* 폴더) Visual Studio 외부에서 클립 아트를 추가 하 고 통합 문서 또는 문서를 저장 합니다.  
  
##  <a name="code"></a> 코드 작성  
 Office 프로젝트에서 코드를 작성할 때 다음과 같은 오류가 발생할 수 있습니다.  
  
### <a name="some-events-of-office-objects-are-not-accessible-when-using-c"></a>C#을 사용 하 여 Office 개체의 일부 이벤트에 액세스할 수 없습니다.  
 경우에 따라 Visual C# 프로젝트에서 Office PIA(주 interop 어셈블리) 형식 인스턴스의 특정 이벤트에 액세스하려고 할 때 다음과 같은 컴파일러 오류가 표시될 수 있습니다.  
  
 "'Microsoft.Office.Interop.Excel._Application.NewWorkbook' 및 'Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook' 간에 모호성이 있습니다."  
  
 이 오류는 개체의 다른 속성 또는 메서드와 이름이 같은 이벤트에 액세스하려는 것을 의미합니다. 이벤트에 액세스 하려면 개체를 캐스팅 해야 해당 *이벤트 인터페이스*합니다.  
  
 이벤트가 있는 Office PIA 형식은 모든 속성 및 메서드를 포함하는 핵심 인터페이스와 개체에 의해 노출되는 이벤트를 포함하는 이벤트 인터페이스 등 두 개의 인터페이스를 구현합니다. 명명 규칙을 사용 하는 이러한 이벤트 인터페이스 *objectname*이벤트*n*_Event을 같은 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> 고 <xref:Microsoft.Office.Interop.Word.ApplicationEvents2_Event>입니다. 개체에 있을 것으로 예상한 이벤트에 액세스할 수 없는 경우 개체를 해당 이벤트 인터페이스로 캐스팅합니다.  
  
 예를 들어 <xref:Microsoft.Office.Interop.Excel.Application> 개체에는 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> 이벤트와 <xref:Microsoft.Office.Interop.Excel._Application.NewWorkbook%2A> 속성이 있습니다. <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.NewWorkbook> 이벤트를 처리하려면 <xref:Microsoft.Office.Interop.Excel.Application>을 <xref:Microsoft.Office.Interop.Excel.AppEvents_Event> 인터페이스로 캐스팅합니다. 다음 코드 예제에서는 Excel용 문서 수준 프로젝트에서 이 작업을 수행하는 방법을 보여 줍니다.  
  
 [!code-csharp[Trin_VstcoreTroubleshootingExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingExcelCS/ThisWorkbook.cs#1)]  
  
 Office Pia의 이벤트 인터페이스에 대 한 자세한 내용은 참조 하세요. [Office 주 interop 어셈블리의 클래스 및 인터페이스 개요](/previous-versions/office/office-12//ms247299(v=office.12))합니다.  
  
### <a name="cannot-reference-office-pia-classes-in-projects-that-target-the-includenetv40shortsharepointincludesnet-v40-short-mdmd-or-the-includenetv45vstoincludesnet-v45-mdmd"></a>수 없습니다. Office PIA 참조의에서 클래스를 프로젝트 대상으로 하는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 또는 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 또는 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]를 대상으로 하는 프로젝트에서는 Office PIA에 정의된 클래스를 참조하는 코드가 기본적으로 컴파일되지 않습니다. 명명 규칙을 사용 하는 Pia에서 클래스 *objectname*클래스와 같이 <xref:Microsoft.Office.Interop.Word.DocumentClass> 고 <xref:Microsoft.Office.Interop.Excel.WorkbookClass>입니다. 예를 들어 Word VSTO 추가 기능 프로젝트의 다음 코드는 컴파일되지 않습니다.  
  
```vb  
Dim document As Word.DocumentClass = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.DocumentClass document = (Word.DocumentClass) Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 이 코드를 실행하면 다음과 같은 컴파일 오류가 발생합니다.  
  
- Visual Basic의 경우: "'있으면 DocumentClass' 클래스에 대 한 참조가 허용 되지 않습니다 해당 어셈블리가 NO-PIA 모드를 사용 하 여 연결 되는 경우."  
  
- Visual C#: "Interop 형식 'Microsoft.Office.Interop.Word.DocumentClass'를 포함할 수 없습니다. 적용 가능한 인터페이스를 대신 사용하세요."  
  
  이 오류를 해결하려면 대신 해당하는 인터페이스를 참조하도록 코드를 수정합니다. 예를 들어 <xref:Microsoft.Office.Interop.Word.DocumentClass> 개체를 참조하는 대신 <xref:Microsoft.Office.Interop.Word.Document> 인터페이스의 인스턴스를 참조합니다.  
  
```vb  
Dim document As Word.Document = Globals.ThisAddIn.Application.ActiveDocument  
```  
  
```csharp  
Word.Document document = Globals.ThisAddIn.Application.ActiveDocument;  
```  
  
 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 또는 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]를 대상으로 하는 프로젝트는 기본적으로 Office PIA의 모든 interop 형식을 자동으로 포함합니다. 이 컴파일 오류는 포함된 interop 형식 기능이 클래스가 아니라 인터페이스에서만 작동하기 때문에 발생합니다. Office Pia의 인터페이스 및 클래스에 대 한 자세한 내용은 참조 하세요. [Office 주 interop 어셈블리의 클래스 및 인터페이스 개요](http://go.microsoft.com/fwlink/?LinkId=189592)합니다. Office 프로젝트에 포함 된 interop 형식 기능에 대 한 자세한 내용은 참조 하세요. [디자인 Office 솔루션을 만들고](../vsto/designing-and-creating-office-solutions.md)합니다.  
  
### <a name="references-to-office-classes-are-not-recognized"></a>Office 클래스에 대 한 참조를 인식 하지 못합니다  
 예를 들어 응용 프로그램의 일부 클래스 이름이 같은 여러 네임 스페이스에 있습니다 <xref:Microsoft.Office.Interop.Word> 고 <xref:System.Windows.Forms>입니다. 이러한 이유로 합니다 **가져오기를**/**사용 하 여** 프로젝트 템플릿 맨 위에 있는 문을 포함 한 간략 한 한정 상수가, 예를 들어:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#2)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#2)]  
  
 이 사용 합니다 **Imports**/**를 사용 하 여** 문에 Word 또는 Excel 한정자를 사용 하 여 Office 클래스에 대 한 참조를 예를 들어 구분 필요:  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#3)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#3](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#3)]  
  
 비정규화된 선언을 사용하는 경우 오류가 발생합니다. 예를 들면 다음과 같습니다.  
  
 [!code-csharp[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreTroubleshootingWordCS/ThisDocument.cs#4)]
 [!code-vb[Trin_VstcoreTroubleshootingWord#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreTroubleshootingWordVB/ThisDocument.vb#4)]  
  
 Word 또는 Excel 네임 스페이스를 가져온을 그 안에 있는 모든 클래스에 대 한 액세스 권한이 있지만 네임 스페이스 모호성을 제거 하려면 Word 또는 Excel을 사용 하 여 모든 형식을 정규화 해야 합니다.  
  
##  <a name="building"></a> 프로젝트 빌드  
 Office 프로젝트를 빌드하면 다음과 같은 오류가 발생할 수 있습니다.  
  
### <a name="cannot-build-a-document-level-project-that-is-based-on-a-document-with-restricted-permissions"></a>제한 된 권한으로 문서를 기반으로 하는 문서 수준 프로젝트를 빌드할 수 없습니다.  
 Visual Studio는 문서에 제한된 권한이 있는 경우 문서 수준 프로젝트를 빌드할 수 없습니다. 제한 된 권한을 가진 문서를 포함 하는 프로젝트, 프로젝트를 컴파일되지 것입니다, 그리고 및에서 다음 메시지가 표시 됩니다 하는 경우는 **오류 목록** 창입니다.  
  
 “사용자 지정을 추가하지 못했습니다.”  
  
 제한된 권한을 가진 문서를 포함하려는 경우 솔루션을 개발 및 빌드하는 동안 무제한 문서를 사용합니다. 그런 다음 솔루션을 게시한 후 게시 위치의 문서에 제한된 권한을 적용합니다.  
  
### <a name="compiler-errors-occur-after-a-namedrange-control-is-deleted"></a>NamedRange 컨트롤이 삭제 된 후 컴파일러 오류 발생  
 디자이너에서 활성 워크시트가 아닌 워크시트에서 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤을 삭제하는 경우 프로젝트에서 자동 생성된 코드를 제거할 수 없으며 컴파일러 오류가 발생할 수 있습니다. 코드를 제거하려면 컨트롤을 삭제하기 전에 항상 <xref:Microsoft.Office.Tools.Excel.NamedRange> 컨트롤이 포함된 워크시트를 선택하여 활성 워크시트로 만들어야 합니다. 컨트롤을 삭제할 때 자동 생성된 코드가 삭제되지 않는 경우 워크시트를 활성화하고 워크시트가 수정된 상태로 표시되도록 내용을 변경하여 디자이너에서 코드를 삭제하게 할 수 있습니다. 프로젝트를 다시 빌드하면 코드가 제거됩니다.  
  
##  <a name="debugging"></a> 프로젝트 디버그  
 Office 프로젝트를 디버그하면 다음과 같은 오류가 발생할 수 있습니다.  
  
### <a name="prompt-to-uninstall-appears-when-you-publish-and-install-a-solution-on-the-development-computer"></a>게시 하 고 개발 컴퓨터에서 솔루션을 설치할 때 제거 메시지가 표시 됩니다.  
 Office 솔루션을 디버그할 때 다음과 같은 오류가 표시될 수 있습니다.  
  
 "다른 버전이 현재 설치되어 있고 이 위치에서 업그레이드할 수 없기 때문에 사용자 지정을 설치할 수 없습니다."  
  
 이 오류는 이전에 개발 컴퓨터에 Office 솔루션을 게시 및 설치했음을 나타냅니다. 메시지를 표시하지 않으려면 솔루션을 디버그하기 전에 컴퓨터에 설치된 프로그램 목록에서 솔루션을 제거합니다. 또는 개발 컴퓨터에서 다른 사용자 계정을 만들어 게시된 솔루션의 설치를 테스트할 수 있습니다.  
  
### <a name="document-level-projects-created-at-unc-network-locations-do-not-run-from-visual-studio"></a>Visual Studio에서 UNC 네트워크 위치에서 만든 문서 수준 프로젝트를 실행 하지 마십시오  
 UNC 네트워크 위치에 Excel 또는 Word용 문서 수준 프로젝트를 만드는 경우 Excel 또는 Word의 신뢰할 수 있는 위치 목록에 문서 위치를 추가해야 합니다. 그렇지 않은 경우 Visual Studio에서 프로젝트를 실행하거나 디버그하려고 하면 사용자 지정이 로드되지 않습니다. 신뢰할 수 있는 위치에 대 한 자세한 내용은 참조 하세요. [문서에 신뢰 부여](../vsto/granting-trust-to-documents.md)합니다.  
  
### <a name="threads-are-not-stopped-correctly-after-debugging"></a>디버깅 후 스레드가 제대로 중지 되지 않습니다.  
 Visual Studio의 Office 프로젝트는 디버거가 프로그램을 제대로 닫을 수 있도록 하는 스레드 명명 규칙을 따릅니다. 솔루션에서 스레드를 만드는 경우 각 스레드의 이름에 접두사 VSTA_를 지정하여 디버깅을 중지할 때 이러한 스레드가 올바르게 처리되도록 해야 합니다. 예를 들어, 설정할 수 있습니다 합니다 `Name` 속성에 대 한 네트워크 이벤트를 기다리는 스레드의 **VSTA_NetworkListener**합니다.  
  
### <a name="cannot-run-or-debug-any-office-solution-on-the-development-computer"></a>실행 하거나 개발 컴퓨터에서 Office 솔루션을 디버깅할 수 없습니다.  
 개발 컴퓨터에서 Office 프로젝트를 실행 또는 개발할 수 없는 경우 다음과 같은 오류 메시지가 표시될 수 있습니다.  
  
 “응용 프로그램 도메인을 만들 수 없으므로 사용자 지정을 로드할 수 없습니다.”  
  
 Visual Studio는 Office 솔루션을 로드하기 전에 .NET Framework 어셈블리 로더인 Fusion을 사용하여 어셈블리를 캐시합니다. Visual Studio가 Fusion 캐시에 쓸 수 있는지 확인한 후 다시 시도합니다. 자세한 내용은 [섀도 복사본 어셈블리](/dotnet/framework/app-domains/shadow-copy-assemblies)합니다.  
  
### <a name="error-when-stopping-the-debugger-in-a-document-level-project-after-using-edit-and-continue"></a>편집 하며 계속 하기를 사용 하 여 문서 수준 프로젝트에서 디버거를 중지 하는 동안 오류가 발생 했습니다.  
 사용 하는 경우 **편집할** 하 고 **계속** 중단 모드에서 프로젝트는 Excel 또는 Word 용 문서 수준 프로젝트에서 코드를 변경 하려면 표시 될 수 하는 경우 다음 오류 메시지가 있는 대화 상자가 있습니다 이후에 디버거를 중지 합니다.  
  
 "현재 상태에서 프로세스를 종료하면 데이터 손실 및 시스템 불안정성을 비롯하여 원치 않는 결과가 발생할 수 있습니다."  
  
 클릭 하는지에 **Yes** 또는 **No** 대화 상자에서 Visual Studio에서 Excel 또는 Word 프로세스를 종료 하 고 디버거를 중지 합니다. 이 대화 상자를 표시하지 않고 프로젝트 디버깅을 중지하려면 Visual Studio에서 디버거를 중지하는 대신 Excel 또는 Word를 직접 종료합니다.  
  
## <a name="see-also"></a>참고자료  
 [Office 솔루션 문제 해결](../vsto/troubleshooting-office-solutions.md)   
 [Office 솔루션 보안 문제 해결](../vsto/troubleshooting-office-solution-security.md)   
 [Office 솔루션 배포 문제 해결](../vsto/troubleshooting-office-solution-deployment.md)  
  
  