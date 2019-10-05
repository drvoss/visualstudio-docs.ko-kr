---
title: '방법: Visual Basic 프로젝트에서 VBA로 코드 노출'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0213df05e12ae69b4e24841971a518acc008599f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419422"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>방법: Visual Basic 프로젝트에서 VBA로 코드 노출
  코드에 노출할 수 있습니다는 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 두 가지 유형의 서로 상호 작용 하는 코드를 원하는 경우 Applications (VBA) 코드에 대 한 Visual basic 프로젝트입니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Visual Basic 프로세스는 Visual C# 프로세스와 다릅니다. 자세한 내용은 [방법: Visual C에서 VBA로 코드 노출&#35; 프로젝트](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)합니다.

 이 과정은 다른 클래스에서 코드에 대 한 것 보다 코드 호스트 항목 클래스에 대 한 다릅니다.

- [호스트 항목 클래스에 코드 노출](#HostItemCode)

- [호스트 항목 클래스에 없는 코드 노출](#NonHostItem)

  ![비디오 링크](../vsto/media/playvideo.gif "비디오 링크") 관련된 비디오 데모를 참조 하세요. [어떻게 할까요? VBA에서 VSTO 코드를 호출할? ](http://go.microsoft.com/fwlink/?LinkId=136757).

## <a name="HostItemCode"></a> 호스트 항목 클래스에 코드 노출
 호스트 항목 클래스에서 Visual Basic 코드를 호출 하는 VBA 코드를 사용 하도록 설정 하려면 설정 합니다 **EnableVbaCallers** 호스트 항목의 속성 **True**합니다.

 호스트 항목 클래스의 메서드를 노출 하 여 VBA에서 호출 하는 방법을 보여 주는 연습을 참조 하세요. [연습: Visual Basic 프로젝트에서 VBA에서 코드를 호출할](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)합니다. 호스트 항목에 대 한 자세한 내용은 참조 하세요. [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)합니다.

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>VBA에 호스트 항목의 코드 노출

1. 문서 수준을 만들거나 열 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Word 문서, Excel 통합 문서 또는 Excel 서식 파일 매크로 지원 하 고 이미 포함 하는 VBA 코드를 기반으로 하는 프로젝트입니다.

     매크로 지 원하는 문서 파일 형식에 대 한 자세한 내용은 참조 하세요. [결합 VBA 및 문서 수준 사용자 지정](../vsto/combining-vba-and-document-level-customizations.md)합니다.

    > [!NOTE]
    > 이 기능은 Word 서식 파일 프로젝트에서 사용할 수 없습니다.

2. 문서의 VBA 코드는 매크로 사용 하도록 설정 하려면 사용자에 게 확인 하지 않고 실행할 수 있는지 확인 합니다. Word 또는 Excel의 보안 센터 설정에서 신뢰할 수 있는 위치 목록에 Office 프로젝트의 위치를 추가하여 VBA 코드를 실행하도록 신뢰할 수 있습니다.

3. 속성, 메서드 또는 프로젝트에서 호스트 항목 클래스 중 하나를 VBA에 노출 하려는 이벤트를 추가 하 고 새 멤버로 선언 **공용**합니다. 클래스의 이름을 응용 프로그램에 따라 달라 집니다.

    - Word 프로젝트에서 호스트 항목 클래스 이름은 `ThisDocument` 기본적으로 합니다.

    - Excel 프로젝트에서 호스트 항목 클래스 라고 `ThisWorkbook`, `Sheet1`를 `Sheet2`, 및 `Sheet3` 기본적으로 합니다.

4. 설정 된 **EnableVbaCallers** 호스트 항목에 대 한 속성 **True**합니다. 이 속성은 사용할 수 있습니다 합니다 **속성** 창 호스트 항목 디자이너에에서 열려 있는 경우.

     이 속성을 설정한 후 Visual Studio 자동으로 설정 하는 **ReferenceAssemblyFromVbaProject** 속성을 **True**합니다.

    > [!NOTE]
    > 통합 문서 또는 문서를 포함 되어 있지 않으면 VBA 코드를 하거나 설정 하는 경우 오류 메시지를 받을 있습니다 문서의 VBA 코드를 실행 하도록 신뢰할 수 없는 경우는 **EnableVbaCallers** 속성을 **True**합니다. 그 이유는 이러한 경우 Visual Studio에서 문서의 VBA 프로젝트를 수정할 수 없기 때문입니다.

5. 표시되는 메시지에서 **확인** 을 클릭합니다. 이 메시지는 알려 동안 문서 또는 통합 문서에 VBA 코드를 추가 하는 경우 프로젝트에서 실행 중인 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], VBA 코드를 손실 됩니다 다음에 프로젝트를 빌드합니다. 즉, 프로젝트를 빌드할 때마다 빌드 출력 폴더에 문서를 덮어씁니다.

     이 시점에서 Visual Studio는 VBA 프로젝트에서 어셈블리를 호출할 수 있도록 프로젝트를 구성 합니다. Visual Studio는 또한 라는 속성을 추가 `CallVSTOAssembly` 에 `ThisDocument`를 `ThisWorkbook`, `Sheet1`를 `Sheet2`, 또는 `Sheet3` VBA 프로젝트에서 모듈입니다. 이 속성을 사용 하 여 VBA에 노출 하는 클래스의 공용 멤버에 액세스할 수 있습니다.

6. 프로젝트를 빌드합니다.

## <a name="NonHostItem"></a> 호스트 항목 클래스에 없는 코드 노출
 호스트 항목 클래스에 없는 Visual Basic 코드를 호출 하는 VBA 코드를 사용 하도록 설정 하려면 VBA에 표시 되므로 코드를 수정 합니다.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>호스트 항목 클래스를 VBA에 없는 코드를 노출 합니다.

1. 문서 수준을 만들거나 열 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] Word 문서, Excel 통합 문서 또는 Excel 서식 파일 매크로 지원 하 고 이미 포함 하는 VBA 코드를 기반으로 하는 프로젝트입니다.

     매크로 지 원하는 문서 파일 형식에 대 한 자세한 내용은 참조 하세요. [결합 VBA 및 문서 수준 사용자 지정](../vsto/combining-vba-and-document-level-customizations.md)합니다.

    > [!NOTE]
    > 이 기능은 Word 서식 파일 프로젝트에서 사용할 수 없습니다.

2. 문서의 VBA 코드는 매크로 사용 하도록 설정 하려면 사용자에 게 확인 하지 않고 실행할 수 있는지 확인 합니다. Word 또는 Excel의 보안 센터 설정에서 신뢰할 수 있는 위치 목록에 Office 프로젝트의 위치를 추가하여 VBA 코드를 실행하도록 신뢰할 수 있습니다.

3. 프로젝트에서 공용 클래스를 VBA에 노출 하려는 멤버를 추가 하 고 새 멤버로 선언 **공용**합니다.

4. 다음 적용 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 고 <xref:Microsoft.VisualBasic.ComClassAttribute> VBA에 노출 되는 클래스에 특성입니다. 이러한 특성 클래스를 VBA에 보이게합니다.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. VBA에 노출할 클래스의 인스턴스를 반환하도록 프로젝트에서 호스트 항목 클래스의 **GetAutomationObject** 메서드를 재정의합니다. 다음 코드 예제에서는 클래스가 노출 한다고 가정 `DocumentUtilities` VBA에 있습니다.

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. 문서 (Word 용) 또는 (Excel 용) 워크시트 디자이너에서 엽니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

7. **속성** 창에서 **ReferenceAssemblyFromVbaProject** 속성을 선택하고 값을 **True**로 변경합니다.

    > [!NOTE]
    > 통합 문서 또는 문서를 포함 되어 있지 않으면 VBA 코드를 하거나 설정 하는 경우 오류 메시지를 받을 있습니다 문서의 VBA 코드를 실행 하도록 신뢰할 수 없는 경우는 **ReferenceAssemblyFromVbaProject** 속성을 **True** . 그 이유는 이러한 경우 Visual Studio에서 문서의 VBA 프로젝트를 수정할 수 없기 때문입니다.

8. 표시되는 메시지에서 **확인** 을 클릭합니다. 이 메시지는 알려 동안 문서 또는 통합 문서에 VBA 코드를 추가 하는 경우 프로젝트에서 실행 중인 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], VBA 코드를 손실 됩니다 다음에 프로젝트를 빌드합니다. 즉, 프로젝트를 빌드할 때마다 빌드 출력 폴더에 문서를 덮어씁니다.

     이 시점에서 Visual Studio는 VBA 프로젝트에서 어셈블리를 호출할 수 있도록 프로젝트를 구성 합니다. Visual Studio는 또한 라는 메서드를 추가 `GetManagedClass` VBA 프로젝트입니다. 어디에서 나이 메서드를 호출할 수에서 VBA 프로젝트를 VBA에 노출 하는 클래스에 액세스 합니다.

9. 프로젝트를 빌드합니다.

## <a name="see-also"></a>참고자료
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office 솔루션을 만들고 디자인](../vsto/designing-and-creating-office-solutions.md)
- [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)
- [연습: Visual Basic 프로젝트에서 VBA에서 코드 호출](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [방법: Visual C에서 VBA로 코드 노출&#35; 프로젝트](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
