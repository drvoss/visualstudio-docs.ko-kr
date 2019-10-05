---
title: '서버 탐색기: SharePoint 연결 노드 확장'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint commands [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bf3d39a8a06a59ed337c0d847bb92875f0f68558
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824159"
---
# <a name="walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension"></a>연습: 서버 탐색기 확장의 SharePoint 클라이언트 개체 모델 호출
  이 연습에 대 한 확장에서 SharePoint 클라이언트 개체 모델을 호출 하는 방법에 설명 합니다 **SharePoint 연결** 노드에서 **서버 탐색기**합니다. SharePoint 클라이언트 개체 모델을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)합니다.

 이 연습에서는 다음 작업을 수행합니다.

- 만들기는 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 을 확장 하는 확장 합니다 **SharePoint 연결** 노드의 **서버 탐색기** 다음과 같은 방법으로:

  - 확장 추가 **웹 파트 갤러리** 에서 SharePoint 사이트 노드가 각 노드에서 **서버 탐색기**합니다. 이 새 노드 사이트의 웹 파트 갤러리에 있는 각 웹 파트를 나타내는 자식 노드를 포함 합니다.

  - 확장은 새로운 유형의 웹 파트 인스턴스를 나타내는 노드를 정의 합니다. 이 새 노드 형식은 아래의 새 자식 노드에 대 한 기반이 됩니다 **웹 파트 갤러리** 노드. 새 웹 파트 노드 형식에 정보를 표시 합니다 **속성** 노드에서 나타내는 웹 파트에 대 한 창.

- 확장을 배포 하는 Visual Studio 확장 (VSIX) 패키지를 빌드합니다.

- 디버깅 및 테스트를 확장 합니다.

> [!NOTE]
> 이 연습에서 만든 확장에서 만든 확장과 비슷합니다 [연습: 웹 파트를 표시 하려면 서버 탐색기 확장](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)합니다. 이 연습에서는 SharePoint 서버 개체 모델을 사용 하지만이 연습에서는 클라이언트 개체 모델을 사용 하 여 동일한 작업을 수행 합니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료 하려면 개발 컴퓨터의 다음 구성 요소가 필요 합니다.

- Windows, SharePoint 및 Visual Studio의 버전을 지원 합니다.

- Visual Studio SDK입니다. 이 연습에서는 합니다 **VSIX 프로젝트** sdk 확장을 배포 하려면 VSIX 패키지를 만드는 템플릿. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)합니다.

다음 개념을 이해에 도움이 필요 하지는 않지만, 연습을 완료 하는:

- SharePoint 클라이언트 개체 모델을 사용 합니다. 자세한 내용은 [관리 클라이언트 개체 모델](http://go.microsoft.com/fwlink/?LinkId=177797)합니다.

- Sharepoint에서 웹 파트입니다. 자세한 내용은 [웹 파트 개요](http://go.microsoft.com/fwlink/?LinkId=177803)합니다.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 두 개의 프로젝트를 만들어야 합니다.

- VSIX 패키지 배포를 만들려면 VSIX 프로젝트를 **서버 탐색기** 확장 합니다.

- 구현 하는 클래스 라이브러리 프로젝트를 **서버 탐색기** 확장 합니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. 에 **새 프로젝트** 대화 상자에서 합니다 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 **확장성**합니다.

    > [!NOTE]
    > 합니다 **확장성** 노드는 Visual Studio SDK를 설치 하는 경우에 사용할 수 있습니다. 자세한 내용은이 항목 앞부분의 전제 조건 섹션을 참조 하세요.

4. 선택 대화 상자 맨 **.NET Framework 4.5** 버전의.NET Framework의 목록에서입니다.

     SharePoint 도구 확장에는이 버전의.NET Framework의 기능이 필요 합니다.

5. 선택 된 **VSIX 프로젝트** 템플릿.

6. 에 **이름** 상자에 입력 **WebPartNode**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **WebPartNode** 프로젝트가 **솔루션 탐색기**합니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 프로젝트**합니다.

2. 에 **새 프로젝트** 대화 상자에서 합니다 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 **Windows**합니다.

3. 선택 대화 상자 맨 **.NET Framework 4.5** 버전의.NET Framework의 목록에서입니다.

4. 프로젝트 템플릿 목록에서 선택 **클래스 라이브러리**합니다.

5. 에 **이름** 상자에 입력 합니다 **WebPartNodeExtension**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **WebPartNodeExtension** 솔루션에 프로젝트를 기본 Class1 코드 파일을 엽니다.

6. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-extension-project"></a>확장 프로젝트를 구성 합니다.
 확장을 만드는 데는 코드를 작성 하기 전에 코드 파일 및 어셈블리 참조를 프로젝트에 추가 해야 하 고 기본 네임 스페이스를 업데이트 해야 합니다.

#### <a name="to-configure-the-project"></a>프로젝트를 구성 하려면

1. 에 **WebPartNodeExtension** 프로젝트 SiteNodeExtension 및 WebPartNodeTypeProvider 코드 파일을 두 개를 추가 합니다.

2. WebPartNodeExtension 프로젝트에 대 한 바로 가기 메뉴를 열고 선택한 **참조 추가**합니다.

3. 에 **참조 관리자-WebPartNodeExtension** 대화 상자를 선택 합니다 **Framework** 노드와 System.ComponentModel.Composition 및 System.Windows.Forms에 대 한 확인란을 선택 어셈블리입니다.

4. 선택 된 **확장** 노드를 각 다음 어셈블리에 대 한 확인란을 선택 하 고 선택한 합니다 **확인** 단추:

    - Microsoft.SharePoint.Client

    - Microsoft.SharePoint.Client.Runtime

    - Microsoft.VisualStudio.SharePoint

5. 바로 가기 메뉴를 열고 합니다 **WebPartNodeExtension** 프로젝트를 선택한 후 **속성**합니다.

     **프로젝트 디자이너**가 열립니다.

6. **애플리케이션** 탭을 선택합니다.

7. 에 **기본 네임 스페이스** 상자 (C#) 또는 **루트 네임 스페이스** (Visual Basic) 상자에 입력 **ServerExplorer.SharePointConnections.WebPartNode**합니다.

## <a name="create-icons-for-the-new-nodes"></a>새 노드에 대 한 아이콘 만들기
 에 대 한 두 아이콘을 만듭니다는 **서버 탐색기** 확장: 새 아이콘 **웹 파트 갤러리** 노드 및 아래에 있는 각 자식 웹 파트 노드에 대 한 다른 아이콘은 **웹 파트 갤러리** 노드입니다. 이 연습의 뒷부분에서는 노드를 사용 하 여 이러한 아이콘을 연결 하는 코드를 작성 합니다.

#### <a name="to-create-icons-for-the-nodes"></a>노드에 대 한 아이콘을 만들려면

1. 에 **프로젝트 디자이너** WebPartNodeExtension 프로젝트를 선택 합니다 **리소스** 탭 합니다.

2. 링크를 선택 **이 프로젝트에 기본 리소스 파일이 없습니다. 기본 리소스 파일을 만들려면 여기를 클릭하십시오.** 를 클릭합니다.

     Visual Studio 리소스 파일을 만들고 디자이너에서 열립니다.

3. 디자이너의 맨 위에 있는 화살표를 선택 합니다 **리소스 추가** 메뉴 명령을 선택한 후 **새 아이콘 추가**합니다.

4. 입력 **WebPartsNode** 새 아이콘에 대 한 이름을 지정 하 고 다음을 선택 합니다 **추가** 단추입니다.

     새 아이콘의 엽니다는 **이미지 편집기**합니다.

5. 쉽게 인식할 수 있는 디자인을 갖도록 아이콘의 16 x 16 버전을 편집 합니다.

6. 아이콘을 32 x 32 버전에 대 한 바로 가기 메뉴를 열고 선택한 **이미지 형식 삭제**합니다.

7. 두 번째 아이콘을 프로젝트 리소스를 추가할 3-7 단계를 반복 하 고이 아이콘의 이름을 **WebPart**합니다.

8. **솔루션 탐색기**의 **리소스** 폴더를 **WebPartNodeExtension** 프로젝트 *WebPartsNode.ico*합니다.

9. 에 **속성** 창을 열려면 합니다 **빌드 작업** 목록 및 선택한 **포함 리소스**합니다.

10. 에 대 한 마지막 두 단계를 반복 *WebPart.ico*합니다.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>서버 탐색기 웹 파트 갤러리 노드 추가
 새 추가 하는 클래스를 만듭니다 **웹 파트 갤러리** 각 SharePoint 사이트 노드가 노드. 클래스를 구현 하는 새 노드를 추가 하 여 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 인터페이스입니다. 기존 노드의 동작을 확장 하려고 할 때마다이 인터페이스를 구현 **서버 탐색기**, 노드에 새 자식 노드를 추가 하는 등입니다.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>서버 탐색기에 웹 파트 갤러리 노드를 추가 하려면

1. 에 다음 코드를 붙여 합니다 **SiteNodeExtension** 코드 파일에 대 한 합니다 **WebPartNodeExtension** 프로젝트.

    > [!NOTE]
    > 이 코드를 추가한 후 프로젝트에 컴파일 오류가 발생 해야 합니다. 이러한 오류가 사라집니다 이후 단계에서 코드를 추가 합니다.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>웹 파트를 나타내는 노드 형식을 정의 합니다.
 새로운 유형의 웹 파트를 나타내는 노드를 정의 하는 클래스를 만듭니다. Visual Studio는 아래에 자식 노드를 표시 하려면이 새 노드 형식을 사용 합니다 **웹 파트 갤러리** 노드. 이러한 자식 노드 각각에 SharePoint 사이트에 단일 웹 파트를 나타냅니다.

 클래스를 구현 하는 새 노드 형식을 정의 하는 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 인터페이스입니다. 에 있는 노드의 새 형식을 정의 하려고 할 때마다이 인터페이스를 구현 **서버 탐색기**합니다.

#### <a name="to-define-the-web-part-node-type"></a>웹 파트 노드 형식을 정의 하려면

1. 에 다음 코드를 붙여 합니다 **WebPartNodeTypeProvider** 코드 파일에 대 한 합니다 **WebPartNodeExtension** 프로젝트.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/CSharp/webpartnode/webpartnodeextension/webpartnodetypeprovider.cs#2)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNode#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnode.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]

## <a name="checkpoint"></a>검사점
 이 시점에서 연습에서는 모든 코드를 **웹 파트 갤러리** 노드는 이제 프로젝트입니다. 빌드를 **WebPartNodeExtension** 프로젝트가 오류 없이 컴파일되는지 확인 합니다.

#### <a name="to-build-the-project"></a>프로젝트를 빌드하려면

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **WebPartNodeExtension** 프로젝트를 선택한 후 **빌드**합니다.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>확장을 배포 하는 VSIX 패키지 만들기
 확장을 배포 하려면 솔루션에서 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. 먼저 프로젝트에 포함 된 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 구성 합니다. 그런 다음 솔루션을 구축 하 여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-the-vsix-package"></a>VSIX 패키지를 구성 하려면

1. **솔루션 탐색기**를 **WebPartNode** 프로젝트를 열고 **source.extension.vsixmanifest** 매니페스트 편집기에서 파일입니다.

     Source.extension.vsixmanifest 파일에는 모든 VSIX 패키지 해야 하는 extension.vsixmanifest 파일에 대 한 기반이 됩니다. 이 파일에 대 한 자세한 내용은 참조 하세요. [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)합니다.

2. 에 **Product Name** 상자에 입력 합니다 **서버 탐색기에 대 한 웹 파트 갤러리 노드**합니다.

3. 에 **작성자** 상자에 입력 합니다 **Contoso**합니다.

4. 에 **설명을** 상자에 입력 합니다 **사용자 지정 웹 파트 갤러리 노드 서버 탐색기에서 SharePoint 연결 노드를 추가**합니다.

5. 에 **자산** 탭 편집기의 선택 된 **새로 만들기** 단추입니다.

6. 에 **새 자산 추가** 대화 상자의 합니다 **형식** 목록에서 선택 **Microsoft.VisualStudio.MefComponent**합니다.

    > [!NOTE]
    > 이 값에 해당 하는 `MefComponent` extension.vsixmanifest 파일의 요소입니다. 이 요소는 VSIX 패키지 확장 어셈블리의 이름을 지정합니다. 자세한 내용은 [MEFComponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))합니다.

7. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.

8. 에 **프로젝트** 목록에서 선택 **WebPartNodeExtension**를 선택한 후는 **확인** 단추입니다.

9. 메뉴 모음에서 **빌드합니다** > **솔루션 빌드**, 솔루션이 오류 없이 컴파일되는지 확인 한 후 확인 합니다.

10. WebPartNode 프로젝트의 빌드 출력 폴더에 이제 WebPartNode.vsix 파일을 포함 해야 합니다.

     빌드 출력 폴더는 기본적으로... 프로젝트 파일이 포함 된 폴더 아래에 있는 \bin\Debug 폴더입니다.

## <a name="test-the-extension"></a>테스트 확장
 이제 새 테스트 준비가 **웹 파트 갤러리** 노드에서 **서버 탐색기**합니다. 먼저, Visual Studio의 실험적 인스턴스에서 확장 프로젝트 디버그를 시작 합니다. 사용 하 여 새 **웹 파트** Visual Studio의 실험적 인스턴스에서 노드.

#### <a name="to-start-debugging-the-extension"></a>디버깅 확장을 시작 하려면

1. 관리자 자격 증명을 사용 하 여 Visual Studio를 다시 시작 하 고 엽니다는 **WebPartNode** 솔루션입니다.

2. WebPartNodeExtension 프로젝트에서 엽니다는 **SiteNodeExtension** 코드 파일을 추가한 다음 중단점에서 코드의 첫 번째 줄에는 `NodeChildrenRequested` 및 `CreateWebPartNodes` 메서드.

3. 선택 된 **F5** 디버깅을 시작 하는 키입니다.

     Visual Studio 서버 Explorer\1.0에 대 한 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web 파트 갤러리 노드 확장에 확장이 설치 되 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에 있는 프로젝트 항목을 테스트할 합니다.

#### <a name="to-test-the-extension"></a>확장을 테스트 하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **뷰** > **서버 탐색기**합니다.

2. 테스트에 사용 하려는 SharePoint에 표시 되는지 확인 합니다 **SharePoint 연결** 노드에서 **서버 탐색기**합니다. 나열 되지 않으면 다음이 단계를 수행 합니다.

    1. 바로 가기 메뉴를 열고 **SharePoint 연결**를 선택한 후 **연결 추가**합니다.

    2. 에 **SharePoint 연결 추가** 대화 상자에 연결 하 고 선택 하려는 SharePoint 사이트에 대 한 URL을 입력 합니다 **확인** 단추.

         개발 컴퓨터에 SharePoint 사이트를 지정 하려면 입력 **http://localhost** 합니다.

3. (표시 하는 사이트의 URL) 사이트 연결 노드를 확장 하 고를 자식 사이트 노드를 확장 (예를 들어 **팀 사이트**).

4. 다른 인스턴스의 Visual Studio의 코드에서 이전에 설정한 중단점에서 중지 확인 합니다 `NodeChildrenRequested` 메서드를 선택한 후 합니다 **F5** 계속 프로젝트를 디버그 하려면 키.

5. Visual Studio의 실험적 인스턴스에서 확장을 **웹 파트 갤러리** 노드는 최상위 사이트 노드 아래에 나타납니다.

6. 다른 인스턴스의 Visual Studio의 코드에서 이전에 설정한 중단점에서 중지 확인 합니다 `CreateWebPartNodes` 메서드를 선택한 후 합니다 **F5** 계속 프로젝트를 디버그 하려면 키.

7. Visual Studio의 실험적 인스턴스에서 연결된 된 사이트의 모든 웹 파트가 나타나는지 확인 합니다 **웹 파트 갤러리** 노드에서 **서버 탐색기**합니다.

8. 웹 파트에 대 한 바로 가기 메뉴를 열고 선택한 **속성**합니다.

9. 에 **속성** 창에서 웹 파트에 대 한 세부 정보 표시 되는지 확인 합니다.

10. **서버 탐색기**, 동일한 웹 파트에 대 한 바로 가기 메뉴를 열고 선택한 후 **메시지를 표시 합니다**합니다.

     표시 되는 메시지 상자를 선택 합니다 **확인** 단추입니다.

## <a name="uninstall-the-extension-from-visual-studio"></a>Visual Studio에서 확장을 제거 합니다.
 확장 테스트를 마친 후 Visual Studio에서 제거 합니다.

#### <a name="to-uninstall-the-extension"></a>확장을 제거하려면

1. 메뉴 모음에서 Visual Studio의 실험적 인스턴스에서 선택 **도구가** > **확장 및 업데이트**합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장의 목록에서 선택 **서버 탐색기에 대 한 웹 파트 갤러리 노드**를 선택한 후 합니다 **제거** 단추입니다.

3. 나타나는 대화 상자에서 선택 합니다 **예** 단추입니다.

4. 선택 된 **지금 다시 시작** 단추 제거를 완료 합니다.

     프로젝트 항목 제거 됩니다.

5. Visual Studio (실험적 인스턴스 및 WebPartNode 솔루션이 열려 있는 Visual Studio의 인스턴스)의 두 인스턴스를 닫습니다.

## <a name="see-also"></a>참고자료
- [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [연습: 웹 파트를 표시 하려면 서버 탐색기 확장](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [아이콘에 대한 이미지 편집기](/cpp/windows/image-editor-for-icons)
- [아이콘 또는 다른 이미지 만들기 &#40;아이콘에 대 한 이미지 편집기&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
