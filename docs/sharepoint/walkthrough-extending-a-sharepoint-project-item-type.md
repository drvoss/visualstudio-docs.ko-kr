---
title: '연습: SharePoint 프로젝트 항목 형식 확장 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 795cc62ca88f7ede87e978d910d397e0ce6e2ad7
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67825980"
---
# <a name="walkthrough-extend-a-sharepoint-project-item-type"></a>연습: SharePoint 프로젝트 항목 형식 확장
  사용할 수는 **비즈니스 데이터 연결 모델** SharePoint에서 비즈니스 데이터 연결 (BDC) 서비스에 대 한 모델을 만드는 프로젝트 항목입니다. 기본적으로이 프로젝트 항목을 사용 하 여 모델을 만들 때 모델의 데이터 표시 되지 않습니다 사용자. 사용자가 데이터를 볼 수 있도록 SharePoint에 외부 목록도 만들어야 합니다.

 이 연습에서는 확장을 만듭니다는 **비즈니스 데이터 연결 모델** 프로젝트 항목입니다. 개발자는 BDC 모델에 데이터를 표시 하는 해당 프로젝트에 외부 목록 만들기에 확장을 사용할 수 있습니다. 이 연습에서는 다음 작업을 수행합니다.

- Visual Studio 확장을 만드는 두 가지 주요 작업을 수행 합니다.

  - BDC 모델의 데이터를 표시 하는 외부 목록을 생성 합니다. 확장 SharePoint 프로젝트 시스템에 대 한 개체 모델을 사용 하 여 생성 하는 *Elements.xml* 목록 정의 하는 파일입니다. 또한 BDC 모델을 함께 배포 될 수 있도록 프로젝트에 파일을 추가 합니다.

  - 바로 가기 메뉴 항목을 추가 합니다 **비즈니스 데이터 연결 모델** 프로젝트의 프로젝트 항목 **솔루션 탐색기**합니다. 개발자는 BDC 모델에 대 한 외부 목록을 생성 하려면이 메뉴 항목 클릭 수 있습니다.

- 확장 프로그램 어셈블리를 배포 하는 Visual Studio 확장 (VSIX) 패키지를 빌드합니다.

- 확장을 테스트 합니다.

## <a name="prerequisites"></a>전제 조건
 이 연습을 완료 하려면 개발 컴퓨터의 다음 구성 요소가 필요 합니다.

- Microsoft Windows, SharePoint, Visual Studio의 버전을 지원 합니다.

- [!include[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)]입니다. 이 연습에서는 합니다 **VSIX 프로젝트** 템플릿 프로젝트 항목을 배포 하려면 VSIX 패키지를 만들려면 sdk에서. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)합니다.

  다음 개념을 이해에 도움이 필요 하지는 않지만, 연습을 완료 하는:

- BDC 서비스에서 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]합니다. 자세한 내용은 [BDC 아키텍처](http://go.microsoft.com/fwlink/?LinkId=177798)합니다.

- BDC 모델에 대 한 XML 스키마입니다. 자세한 내용은 [BDC 모델 인프라](http://go.microsoft.com/fwlink/?LinkId=177799)합니다.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 두 프로젝트를 만들어야 합니다.

- 프로젝트 항목 확장을 배포 하려면 VSIX 패키지를 만들려면 VSIX 프로젝트입니다.

- 프로젝트 항목 확장을 구현 하는 클래스 라이브러리 프로젝트.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 합니다 **확장성** 노드.

    > [!NOTE]
    > 합니다 **확장성** 노드는 Visual Studio SDK를 설치 하는 경우에 사용할 수 있습니다. 자세한 내용은이 항목 앞부분의 전제 조건 섹션을 참조 하세요.

4. 맨 위에 있는 목록에는 **새 프로젝트** 대화 상자에서 **.NET Framework 4.5**합니다.

     SharePoint 도구 확장에는이 버전의.NET Framework의 기능이 필요 합니다.

5. 선택 된 **VSIX 프로젝트** 템플릿.

6. 에 **이름** 상자에 입력 합니다 **GenerateExternalDataLists**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **GenerateExternalDataLists** 프로젝트가 **솔루션 탐색기**합니다.

7. Source.extension.vsixmanifest 파일 자동으로 열리지 GenerateExternalDataLists 프로젝트의 바로 가기 메뉴를 열고 선택한 후 **열기**

8. Source.extension.vsixmanifest 파일 비어 있지 않은 항목이 있는지 확인 합니다 (Contoso 입력) 작성자 필드에 대 한 파일을 저장 한 다음 닫습니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **GenerateExternalDataLists** 솔루션 노드를 선택 **추가**를 선택한 후 **새프로젝트**.

2. 에 **새 프로젝트 추가** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 합니다 **Windows** 노드.

3. 대화 상자의 맨 위에 있는 목록에서 선택 **.NET Framework 4.5**합니다.

4. 프로젝트 템플릿 목록에서 선택 **클래스 라이브러리**합니다.

5. 에 **이름** 상자에 입력 합니다 **BdcProjectItemExtension**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **BdcProjectItemExtension** 솔루션에 프로젝트를 기본 Class1 코드 파일을 엽니다.

6. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-extension-project"></a>확장 프로젝트를 구성 합니다.
 프로젝트 항목 확장을 만드는 데는 코드를 작성 하기 전에 코드 파일과 확장 프로젝트에 대 한 어셈블리 참조를 추가 합니다.

#### <a name="to-configure-the-project"></a>프로젝트를 구성 하려면

1. BdcProjectItemExtension 프로젝트에서 다음 이름을 포함 하는 코드 파일을 두 개를 추가 합니다.

    - ProjectItemExtension

    - GenerateExternalDataLists

2. BdcProjectItemExtension 프로젝트를 선택한 다음, 메뉴 모음의 **프로젝트** > **참조 추가**합니다.

3. 아래는 **어셈블리** 노드를 선택 합니다 **Framework** 노드와 각 다음 어셈블리에 대 한 확인란을 선택:

    - System.ComponentModel.Composition

    - WindowsBase

4. 아래는 **어셈블리** 노드를 선택 합니다 **확장** 노드와 다음 어셈블리에 대 한 확인란을 선택:

    - Microsoft.VisualStudio.SharePoint

5. **확인** 단추를 선택합니다.

## <a name="define-the-project-item-extension"></a>프로젝트 항목 확장을 정의 합니다.
 만들기에 대 한 확장을 정의 하는 클래스를 **비즈니스 데이터 연결 모델** 프로젝트 항목입니다. 확장을 구현 하는 클래스를 정의 하는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> 인터페이스입니다. 프로젝트 항목의 기존 형식을 확장할 하려고 할 때마다이 인터페이스를 구현 합니다.

#### <a name="to-define-the-project-item-extension"></a>프로젝트 항목 확장을 정의 하려면

1. ProjectItemExtension 코드 파일에 다음 코드를 붙여넣습니다.

    > [!NOTE]
    > 이 코드를 추가한 후 프로젝트에 컴파일 오류가 발생 해야 합니다. 이러한 오류가 사라집니다 이후 단계에서 코드를 추가 합니다.

     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/projectitemextension.cs#1)]
     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#1](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/projectitemextension.vb#1)]

## <a name="create-the-external-data-lists"></a>외부 데이터 목록 만들기
 부분 정의 추가 합니다 `GenerateExternalDataListsExtension` BDC 모델의 각 엔터티에 대 한 외부 데이터 목록을 만드는 클래스입니다. 외부 데이터 목록을 만들려면이 코드는 BDC 모델 파일의 XML 데이터를 구문 분석 하 여 BDC 모델의 엔터티 데이터를 먼저 읽습니다. 그런 다음 BDC 모델을 기반으로 하는 프로젝트에이 목록 인스턴스를 추가 하는 목록 인스턴스를 만듭니다.

#### <a name="to-create-the-external-data-lists"></a>외부 데이터를 만들기 위해 나열

1. GenerateExternalDataLists 코드 파일에 다음 코드를 붙여넣습니다.

     [!code-vb[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/VisualBasic/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.vb#2)]
     [!code-csharp[SPExtensibility.ProjectItemExtension.BDCGenerateExternalDataLists#2](../sharepoint/codesnippet/CSharp/generateexternaldatalists/bdcprojectitemextension/generateexternaldatalists.cs#2)]

## <a name="checkpoint"></a>검사점
 이 연습에서는 프로젝트 항목 확장에 대 한 모든 코드 프로젝트에 포함 되었습니다. 프로젝트가 오류 없이 컴파일되는지 확인 솔루션을 빌드하십시오.

#### <a name="to-build-the-solution"></a>솔루션을 빌드하려면

1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

## <a name="create-a-vsix-package-to-deploy-the-project-item-extension"></a>프로젝트 항목 확장을 배포 하려면 VSIX 패키지 만들기
 확장을 배포 하려면 솔루션에서 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. VSIX 프로젝트에 포함 된 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 먼저 구성 합니다. 그런 다음 솔루션을 구축 하 여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-and-create-the-vsix-package"></a>VSIX 패키지를 만들고 구성 하려면

1. **솔루션 탐색기**선택한을 GenerateExternalDataLists 프로젝트에서 source.extension.vsixmanifest 파일에 대 한 바로 가기 메뉴를 열고 **엽니다**합니다.

     Visual Studio 매니페스트 편집기에서 파일을 엽니다. Source.extension.vsixmanifest 파일 모든 VSIX 패키지에 필요한 extension.vsixmanifest 파일에 대 한 기준입니다. 이 파일에 대 한 자세한 내용은 참조 하세요. [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)합니다.

2. 에 **Product Name** 상자에 입력 합니다 **외부 데이터 목록 생성기**합니다.

3. 에 **작성자** 상자에 입력 합니다 **Contoso**합니다.

4. 에 **설명을** 상자에 입력 합니다 **외부 데이터 목록을 생성 하는 비즈니스 데이터 연결 모델 프로젝트 항목에 대 한 확장**합니다.

5. 에 **자산** 탭 편집기의 선택 된 **새로 만들기** 단추입니다.

     합니다 **새 자산 추가** 대화 상자가 나타납니다.

6. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.MefComponent**합니다.

    > [!NOTE]
    > 이 값에 해당 하는 `MefComponent` extension.vsixmanifest 파일의 요소입니다. 이 요소는 VSIX 패키지 확장 어셈블리의 이름을 지정합니다. 자세한 내용은 [MEFComponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))합니다.

7. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.

8. 에 **프로젝트** 목록에서 선택 **BdcProjectItemExtension**를 선택한 후는 **확인** 단추입니다.

9. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

10. 프로젝트를 컴파일하고 빌드 오류가 있는지 확인 합니다.

11. GenerateExternalDataLists 프로젝트의 빌드 출력 폴더에 이제 GenerateExternalDataLists.vsix 파일을 포함 해야 합니다.

     빌드 출력 폴더는 기본적으로... 프로젝트 파일이 포함 된 폴더 아래에 있는 \bin\Debug 폴더입니다.

## <a name="test-the-project-item-extension"></a>테스트 프로젝트 항목 확장
 이제 프로젝트 항목 확장을 테스트할 준비가 되었습니다. 먼저, Visual Studio의 실험적 인스턴스에서 확장 프로젝트를 디버깅 합니다. 그런 다음 BDC 모델에 대 한 외부 목록을 생성 하려면 Visual Studio의 실험적 인스턴스에서 확장을 사용 합니다. 마지막으로 외부 목록을 예상 대로 작동 하는지 확인 하려면 SharePoint 사이트를 엽니다.

#### <a name="to-start-debugging-the-extension"></a>디버깅 확장을 시작 하려면

1. 필요한 경우 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작 하 고 GenerateExternalDataLists 솔루션을 엽니다.

2. BdcProjectItemExtension 프로젝트에서 ProjectItemExtension 코드 파일을 열고 다음 코드 줄에 중단점을 추가 합니다 `Initialize` 메서드.

3. GenerateExternalDataLists 코드 파일을 열고 다음 코드의 첫 번째 줄에 중단점을 추가 합니다 `GenerateExternalDataLists_Execute` 메서드.

4. 선택 하 여 디버깅을 시작 합니다 **F5** 키 또는 메뉴 모음에서 **디버그** > **디버깅 시작**합니다.

     Visual Studio 데이터 목록 Generator\1.0 %UserProfile%\AppData\Local\Microsoft\VisualStudio\10.0Exp\Extensions\Contoso\External에 확장이 설치 되 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에 있는 프로젝트 항목을 테스트 합니다.

#### <a name="to-test-the-extension"></a>확장을 테스트 하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **파일** > **새로 만들기** > **프로젝트**합니다.

2. **새 프로젝트** 대화 상자에서 **템플릿** 노드를 확장 합니다 **Visual C#** 노드를 확장 합니다 **SharePoint** 노드를 차례로 선택할 **2010**합니다.

3. 대화 상자의 맨 위에 있는 목록에서 했는지 **.NET Framework 3.5** 을 선택 합니다. 에 대 한 프로젝트 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 이 버전의.NET Framework가 필요 합니다.

4. 프로젝트 템플릿 목록에서 선택 **SharePoint 2010 프로젝트**합니다.

5. 에 **이름** 상자에 입력 합니다 **SharePointProjectTestBDC**를 선택한 후는 **확인** 단추입니다.

6. SharePoint 사용자 지정 마법사에서에서 디버깅을 위해 사용 하려는 사이트의 URL을 입력 **팜 솔루션으로 배포**를 선택한 후 합니다 **마침** 단추입니다.

7. SharePointProjectTestBDC 프로젝트에 대 한 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 항목**합니다.

8. 에 **NewItem 추가-SharePointProjectTestBDC** 대화 상자, 설치 된 언어 노드를 확장 하 고는 **SharePoint** 노드.

9. 선택 된 **2010** 노드를 선택한 후는 **비즈니스 데이터 연결 모델 (팜 솔루션에만 해당)** 템플릿.

10. 에 **이름** 상자에 입력 합니다 **TestBDCModel**를 선택한 후는 **추가** 단추입니다.

11. Visual Studio의 다른 인스턴스에 코드에 설정한 중단점에서 중지 확인을 `Initialize` ProjectItemExtension 코드 파일의 메서드.

12. Visual Studio의 중지 된 인스턴스를 선택 합니다 **F5** 키 또는 메뉴 모음에서 **디버그** > **계속** 프로젝트 디버깅 합니다.

13. Visual Studio의 실험적 인스턴스를 선택 합니다 **F5** 키 또는 메뉴 모음에서 **디버그** > **디버깅 시작** 을 빌드, 배포 및 실행 합니다 **TestBDCModel** 프로젝트입니다.

     웹 브라우저에서 디버깅을 위해 지정 된 SharePoint 사이트의 기본 페이지로 열립니다.

14. 있는지 확인 합니다 **나열** 빠른 실행 영역에서 섹션 프로젝트의 기본 BDC 모델을 기반으로 하는 목록을 아직 포함 하지 않습니다. SharePoint 사용자 인터페이스를 사용 하 여 또는 프로젝트 항목 확장을 사용 하 여 외부 데이터 목록을 만들어야 합니다.

15. 웹 브라우저를 닫습니다.

16. TestBDCModel 프로젝트 열려 있는 Visual Studio 인스턴스의 바로 가기 메뉴를 열고 합니다 **TestBDCModel** 에서 노드 **솔루션 탐색기**를 선택한 후 **외부 데이터 생성 목록**합니다.

17. Visual Studio의 다른 인스턴스에 코드에 설정한 중단점에서 중지 확인을 `GenerateExternalDataLists_Execute` 메서드. 선택 합니다 **F5** 키 또는 메뉴 모음에서 **디버그** > **계속** 프로젝트를 디버깅 합니다.

18. Visual Studio의 실험적 인스턴스에서 이라고 하는 목록 인스턴스를 추가 **Entity1DataList** 는 TestBDCModel 인스턴스와 프로젝트도 생성 이라고 하는 기능 **Feature2** 목록은 인스턴스입니다.

19. 선택 된 **F5** 키 또는 메뉴 모음에서 **디버그** > **디버깅 시작** 을 빌드, 배포 및 TestBDCModel 프로젝트를 실행 합니다.

     웹 브라우저에서 디버깅에 사용 되는 SharePoint 사이트의 기본 페이지로 열립니다.

20. 에 **나열** 섹션의 빠른 실행 영역을 선택 합니다 **Entity1DataList** 목록.

21. 목록 열 이름이 지정 된 Identifier1 및 메시지는 Identifier1 값 0과 Hello world 메시지 값에는 하나의 항목 외에도 있는지 확인 합니다.

     합니다 **비즈니스 데이터 연결 모델** 프로젝트 템플릿은이 모든 데이터를 제공 하는 기본 BDC 모델을 생성 합니다.

22. 웹 브라우저를 닫습니다.

## <a name="clean-up-the-development-computer"></a>개발 컴퓨터 정리
 프로젝트 항목 확장 테스트를 마친 후 SharePoint 사이트에서 외부 목록 및 BDC 모델을 제거 하 고 Visual Studio에서 프로젝트 항목 확장을 제거 합니다.

#### <a name="to-remove-the-external-data-list-from-the-sharepoint-site"></a>SharePoint 사이트에서 외부 데이터 목록을 제거 하려면

1. SharePoint 사이트의 빠른 실행 영역을 선택 합니다 **Entity1DataList** 목록입니다.

2. SharePoint 사이트에서 리본 메뉴에서 선택 합니다 **목록** 탭 합니다.

3. 에 **목록** 탭의 **설정** 그룹에서 **목록 설정**.

4. 아래 **사용 권한 및 관리**, 선택 **이 목록을 삭제**를 선택한 후 **확인** 목록 휴지통으로 보낼 것임을 확인 하려면.

5. 웹 브라우저를 닫습니다.

#### <a name="to-remove-the-bdc-model-from-the-sharepoint-site"></a>SharePoint 사이트에서 BDC 모델을 제거 하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **빌드합니다** > **Retract**합니다.

     Visual Studio는 SharePoint 사이트에서 BDC 모델을 제거합니다.

#### <a name="to-remove-the-project-item-extension-from-visual-studio"></a>Visual Studio에서 프로젝트 항목 확장을 제거 하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **도구가** > **확장 및 업데이트**합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장의 목록에서 선택 **외부 데이터 목록 생성기**를 선택 합니다 **제거** 단추입니다.

3. 나타나는 대화 상자에서 선택 **예** 확장을 제거할 것인지 확인 합니다.

4. 선택할 **지금 다시 시작** 제거를 완료 합니다.

5. Visual Studio (실험적 인스턴스 및 GenerateExternalDataLists 솔루션 열기의 인스턴스)의 두 인스턴스를 닫습니다.

## <a name="see-also"></a>참고자료
- [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)
- [비즈니스 데이터 연결 모델 만들기](../sharepoint/creating-a-business-data-connectivity-model.md)
- [비즈니스 데이터 연결 모델 디자인](../sharepoint/designing-a-business-data-connectivity-model.md)
