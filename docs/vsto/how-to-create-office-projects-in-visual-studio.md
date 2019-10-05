---
title: '방법: Visual Studio에서 Office 프로젝트 만들기'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.SelectDocWizard.Page1
- VST.SelectDocWizard.Http
- VST.SelectDocWizard.Extension
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], creating projects
- Office applications [Office development in Visual Studio], creating
- Office projects [Office development in Visual Studio]
- projects [Office development in Visual Studio], creating
- document-level customizations [Office development in Visual Studio], creating
- application-level add-ins [Office development in Visual Studio], creating projects
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e41b7714ce5f9a98e50092c1507457b848201773
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419608"
---
# <a name="how-to-create-office-projects-in-visual-studio"></a>방법: Visual Studio에서 Office 프로젝트 만들기
  사용할 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 만들려면 vsto 추가 기능과 문서 수준 사용자 지정 Microsoft Office 응용 프로그램에 대 한 합니다. 이러한 형식의 프로젝트에 대 한 자세한 내용은 참조 하세요. [Office 솔루션 개발 개요 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)합니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-create-a-vsto-add-in-project"></a>VSTO 추가 기능 프로젝트를 만들려면

1. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 차례로 선택합니다. 통합된 개발 환경 (IDE) 사용 하도록 설정 되어 있으면 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 개발 설정에는 **파일** 메뉴에서 선택 **새로 만들기** > **프로젝트**합니다.

    **새 프로젝트** 대화 상자가 나타납니다.

   > [!NOTE]
   > 기본적으로 Office 프로젝트는 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]을(를) 대상으로 합니다. 자세한 내용은 [.NET Framework 클라이언트 프로필](/dotnet/framework/deployment/client-profile)합니다.

2. 를 사용 하려는 언어 노드 아래의 템플릿 창에서 확장 **Office/SharePoint**합니다.

3. 선택 된 **Office 추가 기능의** 노드.

4. 프로젝트 템플릿 목록에서 VSTO 추가 기능 프로젝트 템플릿을 선택합니다. 프로젝트 템플릿 VSTO 추가 기능을 사용할 수 있는 목록을 참조 하세요 [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)합니다.

   > [!NOTE]
   > 프로젝트 템플릿이 표시 되지 않는 경우 선택 하면 합니다 **Office 추가 기능** 노드를 했는지 **.NET Framework 4** 이상이 대화 상자의 맨 위에 있는 콤보 상자에서 선택 합니다. 두 .NET Framework 버전에 대해 모두 Office 프로젝트 템플릿이 표시됩니다.

5. 에 **이름을** 상자, 프로젝트의 이름을 입력 합니다. 기본적으로 프로젝트 이름은 솔루션 이름으로도 사용됩니다.

6. 에 **위치** 상자에 프로젝트를 만들려면 원하는 경로 입력 합니다. 절대 경로와 UNC(범용 명명 규칙) 경로를 사용할 수 있습니다. HTTP, FTP 또는 기타 프로토콜 경로 사용하지 마세요.

    위치 형식은 다음과 같습니다.

   * [*drive*\]\:

   * \\\\*서버*\\*공유*

     위치에 다음 문자를 사용하지 마세요.

   * *(별표)

   * 세로 막대(|)

   * 콜론(:)(드라이브 문자 뒤에는 제외)

   * 큰따옴표(")(공백이 포함된 경로에는 따옴표가 필요하지 않음)

   * 보다 작음(\<)

   * 보다 큼(>)

   * 물음표(?)

   * 백분율 기호(%)

7. **확인** 단추를 선택합니다.

   ::: moniker range="vs-2017"

   > [!NOTE]
   > 추가 기능 프로젝트는 생성될 때 항상 저장됩니다. 이 프로젝트를 임시 프로젝트로 만들 수 없습니다. 임시 프로젝트에 대 한 자세한 내용은 참조 하세요. [임시 프로젝트](../ide/creating-solutions-and-projects.md#create-a-temporary-project)합니다.

   ::: moniker-end

### <a name="to-create-a-document-level-customization-project"></a>문서 수준 사용자 지정 프로젝트를 만들려면

1. **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 차례로 선택합니다. Visual Basic 개발 설정을 사용 하려면 IDE에 설정 된 경우는 **파일** 메뉴 선택 **새로 만들기** > **프로젝트**합니다.

    **새 프로젝트** 대화 상자가 나타납니다.

2. 를 사용 하려는 언어 노드 아래의 템플릿 창에서 확장 **Office/SharePoint**합니다.

3. **Office 추가 기능** 노드를 선택합니다.

4. 프로젝트 템플릿 목록에서 문서 수준 프로젝트 템플릿을 선택합니다. 사용 가능한 문서 수준 프로젝트 템플릿 목록은 참조 하세요. [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)합니다.

   > [!NOTE]
   > 프로젝트 템플릿이 표시 되지 않는 경우 선택 하면 합니다 **Office 추가 기능** 노드를 했는지 **.NET Framework 4** 이상이 선택 합니다.

5. 에 **이름을** 상자, 프로젝트의 이름을 입력 합니다. 기본적으로 이 이름은 문서에도 사용됩니다. IDE가 Visual C# 개발 설정이나 일반 개발 설정을 사용하도록 설정되면 위치 및 솔루션 이름도 입력합니다.

   > [!NOTE]
   > 프로젝트 위치 경로 또는 프로젝트 이름에는 서로게이트 문자를 사용할 수 없습니다. 솔루션을 오프라인에서 사용하도록 배포하려면 프로젝트 이름의 문자가 HTTP 프로토콜 사양에 맞아야 합니다.

6. **확인** 단추를 선택합니다.

    **Visual Studio Tools for Office 프로젝트 마법사** 가 열립니다.

7. 선택 **새 문서를 만듭니다** 솔루션에 대 한 새 문서 만들기 또는 선택 하려는 경우 **기존 문서 복사** 기존 문서를 사용자 지정 하려는 경우.

    새 문서를 만드는 경우에 이름을 지정 합니다 **이름** 상자를 사용 하 여 문서 형식을 선택 합니다 **형식** 상자입니다. 사용 가능한 형식에 대 한 자세한 내용은 참조 하세요. [의 문서 수준 사용자 지정 아키텍처](../vsto/architecture-of-document-level-customizations.md)합니다.

    기존 문서를 사용 하는 경우에 있는 문서의 위치를 지정 합니다 **기존 문서의 전체 경로** 상자입니다. 절대 경로와 UNC 경로를 사용할 수 있습니다. 문서에 대한 HTTP, FTP 또는 기타 프로토콜 경로 사용하지 마세요.

    위치 형식은 다음과 같습니다.

   - [*drive*\]\:

   - \\\\*서버*\\*공유*

     위치에 다음 문자를 사용하지 마세요.

   - *(별표)

   - 세로 막대(|)

   - 콜론(:)(드라이브 문자 뒤에는 제외)

   - 큰따옴표(")(공백이 포함된 경로에는 따옴표가 필요하지 않음)

   - 보다 작음(\<)

   - 보다 큼(>)

   - 물음표(?)

   - 백분율 기호(%)

   > [!NOTE]
   > [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 프로젝트에서 기존 문서를 사용할 경우 [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]에서 생성되거나 해당 항목으로 변환된 문서만 사용하세요. 마찬가지로 Word 2010 프로젝트의 기존 문서를 사용할 경우 Word 2010에서 생성되거나 해당 항목으로 변환된 문서만 사용하세요. 이전 버전 Word에서 생성된 문서를 사용하면 문서에서 특정 기능이 사용하지 않도록 설정됩니다. 이들 기능을 사용하는 코드를 작성하려고 하면 프로젝트에서 오류가 발생할 수 있습니다. 문서를 변환 하려면에서 엽니다 [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 또는 Word 2010에는 **파일** 리본의 탭을 선택 **정보** > **변환**합니다.

8. **마침**을 선택합니다.

9. 다음 경우에 Word의 보안 센터에 있는 신뢰할 수 있는 위치 목록에 프로젝트 폴더와 하위 폴더를 추가합니다.

   - 만드는 기반으로 하는 Word 문서를 *.docm* VBA 프로젝트가 포함 된 파일 및 문서 또는 Windows Forms 컨트롤을 호스트 합니다. 신뢰할 수 있는 위치 목록에 프로젝트 폴더를 추가하면 디자인 타임에 문서가 예상대로 작동하는지 확인할 수 있습니다.

   - 기반이 되는 Word 서식 파일 프로젝트를 만들면를 *.dotx* 파일입니다. 프로젝트를 실행하고 디버그할 수 있도록 신뢰할 수 있는 위치 목록에 프로젝트 폴더를 추가해야 합니다.

     신뢰할 수 있는 위치에 문서를 추가 하는 방법에 대 한 자세한 내용은 Microsoft Office 온라인 웹 사이트를 참조 하세요 [만들기, 제거 또는 변경 프로그램 파일에 대 한 신뢰할 수 있는 위치](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62)합니다.

## <a name="see-also"></a>참고자료
- [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)
- [Office 솔루션 공동 개발](../vsto/collaborative-development-of-office-solutions.md)
- [Office 솔루션을 만들고 디자인](../vsto/designing-and-creating-office-solutions.md)
- [VSTO 추가 기능 프로그래밍 시작](../vsto/getting-started-programming-vsto-add-ins.md)
