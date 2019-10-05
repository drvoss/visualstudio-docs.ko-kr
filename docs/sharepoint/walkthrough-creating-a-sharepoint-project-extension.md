---
title: '연습: SharePoint 프로젝트 확장명 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 10affe50b3410fa013205313f4087aaabb7c4769
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825796"
---
# <a name="walkthrough-create-a-sharepoint-project-extension"></a>연습: SharePoint 프로젝트 확장명 만들기
  이 연습에는 SharePoint 프로젝트 확장을 만드는 방법을 보여 줍니다. 프로젝트를 추가, 삭제 또는 이름이 같은 프로젝트 수준 이벤트에 응답 하는 프로젝트 확장명을 사용할 수 있습니다. 사용자 지정 속성을 추가 하거나 속성 값이 변경 될 때 응답할 수도 있습니다. 프로젝트 항목 확장 달리 프로젝트 확장명을 특정 SharePoint 프로젝트 형식과 사용 하 여 연결할 수 없습니다. 확장 로드에서 모든 종류의 SharePoint 프로젝트를 열면 프로젝트 확장을 만들면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

 이 연습에서 만든 모든 SharePoint 프로젝트에 추가 되는 사용자 지정 부울 속성을 만들게 됩니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. 로 설정 하면 **True**, 새 속성 추가, 또는 맵, 이미지 리소스 폴더를 사용 하 여 프로젝트를 합니다. 로 설정 하면 **False**, 있는 경우 이미지 폴더 제거 됩니다. 자세한 내용은 [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)합니다.

 이 연습에서는 다음 작업을 수행합니다.

- 만들기는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint 프로젝트에 다음을 수행 하는 확장 합니다.

  - 속성 창에 사용자 지정 프로젝트 속성을 추가합니다. SharePoint 프로젝트에 속성이 적용 됩니다.

  - 프로젝트에 매핑된 폴더를 추가할 SharePoint 프로젝트 개체 모델을 사용 합니다.

  - 사용 하 여 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 자동화 개체 모델 (DTE) 프로젝트의 매핑된 폴더를 삭제 하려면.

- 빌드를 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 프로젝트 속성의 확장 프로그램 어셈블리를 배포 하려면 VSIX (Extension) 패키지 있습니다.

- 디버깅 및 프로젝트 속성을 테스트 합니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료 하려면 개발 컴퓨터의 다음 구성 요소가 필요 합니다.

- 지원 되는 버전 [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)], SharePoint 및 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

- [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]입니다. 이 연습에서는 합니다 **VSIX 프로젝트** 에서 템플릿을 [!INCLUDE[TLA2#tla_sdk](../sharepoint/includes/tla2sharptla-sdk-md.md)] 프로젝트 속성 확장 프로그램을 배포 하려면 VSIX 패키지를 만듭니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 두 개의 프로젝트를 만들어야 합니다.

- 프로젝트 확장을 배포 하려면 VSIX 패키지를 만들려면 VSIX 프로젝트입니다.

- 프로젝트 확장을 구현 하는 클래스 라이브러리 프로젝트.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 합니다 **확장성** 노드.

    > [!NOTE]
    > 이 노드는 Visual Studio SDK를 설치 하는 경우에 사용할 수 있습니다. 자세한 내용은이 항목 앞부분의 전제 조건 섹션을 참조 하세요.

4. 선택 대화 상자의 맨 위에 있는 **.NET Framework 4.5** 버전의.NET Framework의 목록에서를 선택 합니다 **VSIX 프로젝트** 템플릿.

5. 에 **이름** 상자에 입력 합니다 **ProjectExtensionPackage**를 선택한 후는 **확인** 단추입니다.

     합니다 **ProjectExtensionPackage** 프로젝트가 표시 됩니다 **솔루션 탐색기**합니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 프로젝트**합니다.

2. 에 **새 프로젝트** 대화 상자에서 합니다 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 **Windows**합니다.

3. 선택 대화 상자 맨 **.NET Framework 4.5** 버전의.NET Framework의 목록에서 선택한 후 합니다 **클래스 라이브러리** 프로젝트 템플릿.

4. 에 **이름** 상자에 입력 합니다 **ProjectExtension**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **ProjectExtension** 솔루션에 프로젝트를 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-project"></a>프로젝트 구성
 프로젝트 확장을 만드는 데는 코드를 작성 하기 전에 코드 파일과 확장 프로젝트에 대 한 어셈블리 참조를 추가 합니다.

#### <a name="to-configure-the-project"></a>프로젝트를 구성 하려면

1. 이라는 코드 파일을 추가 **CustomProperty** ProjectExtension 프로젝트입니다.

2. 바로 가기 메뉴를 열고 합니다 **ProjectExtension** 프로젝트를 선택한 후 **참조 추가**합니다.

3. 에 **참조 관리자-CustomProperty** 대화 상자를 선택 합니다 **프레임 워크** 노드와 System.ComponentModel.Composition 및 System.Windows.Forms 어셈블리 옆의 확인란을 선택 합니다.

4. 선택 합니다 **확장** 노드를 Microsoft.VisualStudio.SharePoint 및 EnvDTE 어셈블리 옆의 확인란을 선택 하 고 선택한 합니다 **확인** 단추입니다.

5. **솔루션 탐색기**아래에 있는 **참조** 폴더를 **ProjectExtension** 프로젝트 **EnvDTE**합니다.

6. 에 **속성** 창에서 변경 합니다 **Interop 형식 포함** 속성을 **False**합니다.

## <a name="define-the-new-sharepoint-project-property"></a>새 SharePoint 프로젝트 속성 정의
 프로젝트 확장 하 고 새 프로젝트 속성의 동작을 정의 하는 클래스를 만듭니다. 클래스를 구현 하는 새 프로젝트 확장을 정의 하는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 인터페이스입니다. SharePoint 프로젝트에 대 한 확장을 정의 하려는 경우이 인터페이스를 구현 합니다. 또한 추가 된 <xref:System.ComponentModel.Composition.ExportAttribute> 클래스입니다. 이 특성을 사용 하면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 검색 하 고 로드 하 여 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 구현 합니다. 전달 된 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> 형식 특성의 생성자입니다.

#### <a name="to-define-the-new-sharepoint-project-property"></a>새 SharePoint 프로젝트 속성을 정의 하려면

1. CustomProperty 코드 파일에 다음 코드를 붙여넣습니다.

     [!code-vb[SPExt_ProjectExtension#1](../sharepoint/codesnippet/VisualBasic/projectextension/customproperty.vb#1)]
     [!code-csharp[SPExt_ProjectExtension#1](../sharepoint/codesnippet/CSharp/projectextension/customproperty.cs#1)]

## <a name="build-the-solution"></a>솔루션 빌드
 다음으로, 오류 없이 컴파일되는지 확인 솔루션을 빌드하십시오.

#### <a name="to-build-the-solution"></a>솔루션을 빌드하려면

1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

## <a name="create-a-vsix-package-to-deploy-the-project-property-extension"></a>프로젝트 속성 확장 프로그램을 배포 하려면 VSIX 패키지 만들기
 프로젝트 확장을 배포 하려면 솔루션에서 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. VSIX 프로젝트에 포함 된 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 먼저 구성 합니다. 그런 다음 솔루션을 구축 하 여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX 패키지를 만들고 구성 하려면

1. **솔루션 탐색기**를 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 열고 선택한 합니다 **엽니다** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 매니페스트 디자이너에서 파일을 엽니다. 에 표시 되는 정보는 **메타 데이터** 탭에도 표시 됩니다는 **확장 및 업데이트**합니다. 모든 VSIX 패키지 extension.vsixmanifest 파일을 필요합니다. 이 파일에 대 한 자세한 내용은 참조 하세요. [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)합니다.

2. 에 **Product Name** 상자에 입력 합니다 **사용자 지정 프로젝트 속성**합니다.

3. 에 **작성자** 상자에 입력 합니다 **Contoso**합니다.

4. 에 **설명을** 상자에 입력 합니다 **프로젝트에 이미지의 리소스 폴더의 매핑을 설정/해제 하는 사용자 지정 SharePoint 프로젝트 속성**합니다.

5. 선택 된 **자산** 탭을 선택한 다음는 **새로 만들기** 단추입니다.

     합니다 **새 자산 추가** 대화 상자가 나타납니다.

6. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.MefComponent**합니다.

    > [!NOTE]
    > 이 값에 해당 하는 `MEFComponent` extension.vsixmanifest 파일의 요소입니다. 이 요소는 VSIX 패키지 확장 어셈블리의 이름을 지정합니다. 자세한 내용은 [MEFComponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))합니다.

7. 에 **원본** 목록에서 선택 합니다 **현재 솔루션의 프로젝트** 옵션 단추입니다.

8. 에 **프로젝트** 목록에서 선택 **ProjectExtension**합니다.

     이 값에는 프로젝트에서 빌드 중인 어셈블리의 이름을 식별 합니다.

9. 선택할 **확인** 닫으려면 합니다 **새 자산 추가** 대화 상자.

10. 메뉴 모음에서 선택 **파일** > **모두 저장** 를 완료 하 고 다음 매니페스트 디자이너를 닫습니다.

11. 메뉴 모음에서 선택 **빌드합니다** > **솔루션 빌드**, 프로젝트가 오류 없이 컴파일되는지 확인 한 후 확인 합니다.

12. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **ProjectExtensionPackage** 프로젝트를 선택한 합니다 **파일 탐색기에서 폴더 열기** 단추.

13. **파일 탐색기**ProjectExtensionPackage 프로젝트의 빌드 출력 폴더를 열고 ProjectExtensionPackage.vsix 라는 파일을 폴더에 포함 되어 있는지 확인 합니다.

     빌드 출력 폴더는 기본적으로... 프로젝트 파일이 포함 된 폴더 아래에 있는 \bin\Debug 폴더입니다.

## <a name="test-the-project-property"></a>프로젝트 속성 테스트
 이제 사용자 지정 프로젝트 속성을 테스트할 준비가 되었습니다. 디버그 하 고 새 프로젝트 속성 확장의 실험적 인스턴스에서 테스트 하는 것이 쉽습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다. 이 인스턴스의 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] VSIX 또는 다른 확장성 프로젝트를 실행할 때 생성 됩니다. 시스템에서 확장을 설치 하 고 디버깅 하 고 일반 인스턴스의 테스트 한 다음 계속 프로젝트를 디버그 후 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

#### <a name="to-debug-and-test-the-extension-in-an-experimental-instance-of-visual-studio"></a>디버깅 하 고 Visual Studio의 실험적 인스턴스에서 확장을 테스트

1. 다시 시작 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 관리자 자격 증명과 ProjectExtensionPackage 솔루션을 엽니다.

2. 선택 하거나 프로젝트의 디버그 빌드를 시작 합니다 **F5** 키 또는 메뉴 모음에서 **디버그** > **디버깅 시작**합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Custom 프로젝트 Property\1.0에 확장을 설치 하 고 실험적 인스턴스의 시작 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

3. 실험적 인스턴스에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]은 팜 솔루션에 대 한 SharePoint 프로젝트를 만들고 마법사의 다른 값에 대 한 기본값을 사용 합니다.

    1. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

    2. 맨 위에 있는 합니다 **새 프로젝트** 대화 상자에서 **.NET Framework 3.5** 버전의.NET Framework의 목록에서.

         SharePoint 도구 확장의이 버전의 기능이 필요 합니다 [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]합니다.

    3. 아래는 **템플릿** 노드를 확장 합니다 **Visual C#** 또는 **Visual Basic** 노드를 선택는 **SharePoint** 노드를를 선택한 다음 합니다 **2010** 노드.

    4. 선택 합니다 **SharePoint 2010 프로젝트** 템플릿을 누릅니다 **ModuleTest** 프로젝트의 이름으로.

4. **솔루션 탐색기**를 선택 합니다 **ModuleTest** 프로젝트 노드.

     새 사용자 지정 속성을 **지도 이미지 폴더** 에 표시 되는 **속성** 의 기본값을 사용 하 여 창 **False**합니다.

5. 이 속성의 값을 변경 **True**합니다.

     이미지 리소스 폴더는 SharePoint 프로젝트에 추가 됩니다.

6. 해당 속성의 값을 다시 변경 **False**합니다.

     원하는 경우는 **예** 단추를 **이미지 폴더를 삭제?** 대화 상자에서 SharePoint 프로젝트의 리소스 폴더를 삭제 하는 이미지입니다.

7. 실험적 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 인스턴스를 닫습니다.

## <a name="see-also"></a>참고자료
- [SharePoint 프로젝트 확장](../sharepoint/extending-sharepoint-projects.md)
- [방법: SharePoint 프로젝트에 속성 추가](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식 간의 변환](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [SharePoint 프로젝트 시스템의 확장에 데이터를 저장 합니다.](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [SharePoint 도구 확장과 사용자 지정 데이터 연결](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
