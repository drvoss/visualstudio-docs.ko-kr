---
title: '방법: VBA로 코드 노출 된 C# 프로젝트'
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ac41f4da29b95ba1fcd1601f98104956d584212a
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419514"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>방법: 시각적 개체에서 VBA로 코드 노출 C# 프로젝트
  두 가지 유형의 서로 상호 작용 하는 코드를 원하는 경우 Visual C# 프로젝트에서 Visual basic Applications (VBA) 코드에 대 한 코드를 노출할 수 있습니다.

 Visual C# 프로세스는 Visual Basic 프로세스와 다릅니다. 자세한 내용은 [방법: Visual Basic 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)합니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Visual C# 프로젝트의 코드 노출
 Visual C# 프로젝트에서 코드를 호출 하는 VBA 코드를 사용 하려면 COM에 노출 되므로 코드를 수정 하 고 설정 합니다 **ReferenceAssemblyFromVbaProject** 속성을 **True** 디자이너에서 합니다.

 시각적 개체에서 메서드를 호출 하는 방법을 보여 주는 연습은 C# 에서 VBA 프로젝트, 참조 [연습: Visual C에서 vba의 코드를 호출할&#35; 프로젝트](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)합니다.

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>에 Visual C# 프로젝트에서 VBA로 코드 노출

1. 열거나 Word 문서, Excel 통합 문서 또는 Excel 서식 파일 매크로 지원 하 고 이미 포함 하는 VBA 코드를 기반으로 하는 문서 수준 프로젝트를 만듭니다.

    매크로 지 원하는 문서 파일 형식에 대 한 자세한 내용은 참조 하세요. [결합 VBA 및 문서 수준 사용자 지정](../vsto/combining-vba-and-document-level-customizations.md)합니다.

   > [!NOTE]
   > 이 기능은 Word 서식 파일 프로젝트에서 사용할 수 없습니다.

2. 문서의 VBA 코드는 매크로 사용 하도록 설정 하려면 사용자에 게 확인 하지 않고 실행할 수 있는지 확인 합니다. Word 또는 Excel의 보안 센터 설정에서 신뢰할 수 있는 위치 목록에 Office 프로젝트의 위치를 추가하여 VBA 코드를 실행하도록 신뢰할 수 있습니다.

3. 프로젝트에서 공용 클래스를 VBA에 노출 하려는 멤버를 추가 하 고 새 멤버로 선언 **공용**합니다.

4. 다음 적용 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 고 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> VBA에 노출 되는 클래스에 특성입니다. 이러한 특성은 클래스가 COM에 표시되도록 하지만 클래스 인터페이스를 생성하지 않습니다.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. 재정의 된 **GetAutomationObject** VBA에 노출할 클래스의 인스턴스를 반환 하기 위해 프로젝트에서 호스트 항목 클래스의 메서드:

   - 호스트 항목 클래스를 VBA에 노출할 경우 재정의 **GetAutomationObject** 메서드는이 클래스에 속하며 클래스의 현재 인스턴스를 반환 합니다.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - VBA에는 호스트 항목이 아닌 클래스를 제공 하는 경우 재정의 **GetAutomationObject** 메서드는 호스트의 프로젝트에서 항목 및 호스트 항목이 아닌 클래스의 인스턴스를 반환 합니다. 예를 들어, 다음 코드를 가정 라는 클래스를 노출할 `DocumentUtilities` VBA에 있습니다.

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     호스트 항목에 대 한 자세한 내용은 참조 하세요. [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)합니다.

6. VBA에 노출할 클래스에서 인터페이스를 추출 합니다. 에 **인터페이스 추출** 대화 상자에서 인터페이스 선언에 포함 하려는 공용 멤버를 선택 합니다. 자세한 내용은 [추출 인터페이스 리팩터링](../ide/reference/extract-interface.md)합니다.

7. 추가 된 **공용** 키워드를 인터페이스 선언 합니다.

8. 다음을 추가 하 여 인터페이스를 COM에 표시 되도록 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 특성을 인터페이스입니다.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. 디자이너에서 문서 (Word 용) 또는 (Excel 용)는 워크시트를 열고 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

10. **속성** 창에서 **ReferenceAssemblyFromVbaProject** 속성을 선택하고 값을 **True**로 변경합니다.

    > [!NOTE]
    > 통합 문서 또는 문서를 포함 되어 있지 않으면 VBA 코드 아니면 설정 하는 경우 오류 메시지를 받을 있습니다 문서의 VBA 코드를 실행 하도록 신뢰할 수 없는 경우는 **ReferenceAssemblyFromVbaProject** 속성을 **True**. 그 이유는 이러한 경우 Visual Studio에서 문서의 VBA 프로젝트를 수정할 수 없기 때문입니다.

11. 표시되는 메시지에서 **확인** 을 클릭합니다. 이 메시지는 알려 추가 하는 경우 VBA 코드를 통합 문서 또는 문서에서 프로젝트를 실행 하는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], VBA 코드를 손실 됩니다 다음 번에 프로젝트를 빌드합니다. 이 문서에 빌드 출력 폴더는 프로젝트를 빌드할 때마다 덮어씁니다 때문입니다.

     이 시점에서 Visual Studio는 VBA 프로젝트에서 어셈블리를 호출할 수 있도록 프로젝트를 구성 합니다. Visual Studio는 또한 라는 메서드를 추가 `GetManagedClass` VBA 프로젝트입니다. 어디에서 나이 메서드를 호출할 수에서 VBA 프로젝트를 VBA에 노출 하는 클래스에 액세스 합니다.

12. 프로젝트를 빌드합니다.

## <a name="see-also"></a>참고자료
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office 솔루션을 만들고 디자인](../vsto/designing-and-creating-office-solutions.md)
- [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)
- [연습: Visual C에서 vba의 코드를 호출할&#35; 프로젝트](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [방법: Visual Basic 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
