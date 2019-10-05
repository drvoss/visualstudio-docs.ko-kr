---
title: '연습: 웹 파트를 표시 하려면 서버 탐색기 확장 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint commands
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
- SharePoint Connections [SharePoint development in Visual Studio], creating a new node type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1c84cfcde4a5ffac1e1563a4d2b141bd6240b772
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821994"
---
# <a name="walkthrough-extend-server-explorer-to-display-web-parts"></a>연습: 웹 파트를 표시 하려면 서버 탐색기 확장
  Visual Studio에서 사용할 수 있습니다 합니다 **SharePoint 연결** 노드의 **서버 탐색기** SharePoint 사이트에서 구성 요소를 볼 수 있습니다. 그러나 **서버 탐색기** 기본적으로 일부 구성 요소를 표시 하지 않습니다. 이 연습에서는 확장할 예정 **서버 탐색기** SharePoint 사이트를 연결 된 각 웹 파트 갤러리에 표시 되도록 합니다.

 이 연습에서는 다음 작업을 수행합니다.

- 확장 하는 Visual Studio 확장을 만들 **서버 탐색기** 다음과 같은 방법으로:

  - 확장 추가 **웹 파트 갤러리** 에서 SharePoint 사이트 노드가 각 노드에서 **서버 탐색기**합니다. 이 새 노드 사이트의 웹 파트 갤러리에 있는 각 웹 파트를 나타내는 자식 노드를 포함 합니다.

  - 확장은 새로운 유형의 웹 파트 인스턴스를 나타내는 노드를 정의 합니다. 이 새 노드 형식은 아래의 새 자식 노드에 대 한 기반이 됩니다 **웹 파트 갤러리** 노드. 새 웹 파트 노드 형식에 정보를 표시 합니다 **속성** 나타내는 웹 파트에 대 한 창. 노드 형식에는 웹 파트와 관련 된 기타 작업을 수행 하는 것에 대 한 시작 점으로 사용할 수 있는 사용자 지정 바로 가기 메뉴 항목을 포함 됩니다.

- 확장 프로그램 어셈블리를 호출 하는 두 개의 사용자 지정 SharePoint 명령을 만듭니다. SharePoint 명령은 Api를 사용 하는 서버 개체 모델에서 SharePoint 용 확장 프로그램 어셈블리에서 호출할 수 있는 메서드입니다. 이 연습에서는 개발 컴퓨터의 로컬 SharePoint 사이트에서 웹 파트 정보를 검색 하는 명령을 만들 수 있습니다. 자세한 내용은 [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)합니다.

- 확장을 배포 하는 Visual Studio 확장 (VSIX) 패키지를 빌드합니다.

- 디버깅 및 테스트를 확장 합니다.

> [!NOTE]
> 다른 버전의 서버 개체 모델에 해당 하는 대신 SharePoint에 대 한 클라이언트 개체 모델을 사용 하는이 연습을 참조 하세요. [연습: 서버 탐색기 확장의 SharePoint 클라이언트 개체 모델을 호출할](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)합니다.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료 하려면 개발 컴퓨터의 다음 구성 요소가 필요 합니다.

- Windows, SharePoint, Visual Studio의 버전을 지원 합니다.

- Visual Studio SDK입니다. 이 연습에서는 합니다 **VSIX 프로젝트** 템플릿 프로젝트 항목을 배포 하려면 VSIX 패키지를 만들려면 sdk에서. 자세한 내용은 [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)합니다.

  다음 개념을 이해에 도움이 필요 하지는 않지만, 연습을 완료 하는:

- SharePoint에 대 한 서버 개체 모델을 사용합니다. 자세한 내용은 [SharePoint Foundation Server 쪽 개체 모델을 사용 하 여](http://go.microsoft.com/fwlink/?LinkId=177796)입니다.

- SharePoint 솔루션에서 웹 파트입니다. 자세한 내용은 [웹 파트 개요](http://go.microsoft.com/fwlink/?LinkId=177803)합니다.

## <a name="create-the-projects"></a>프로젝트 만들기
 이 연습을 완료 하려면 세 개의 프로젝트를 만들어야 합니다.

- 확장을 배포 하려면 VSIX 패키지를 만들려면 VSIX 프로젝트입니다.

- 확장을 구현 하는 클래스 라이브러리 프로젝트. 이 프로젝트는.NET Framework 4.5를 대상으로 해야 합니다.

- 사용자 지정 SharePoint 명령을 정의 하는 클래스 라이브러리 프로젝트. 이 프로젝트는 the.NET Framework 3.5를 대상 해야 합니다.

  프로젝트를 만들어 연습을 시작 합니다.

#### <a name="to-create-the-vsix-project"></a>VSIX 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. 메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 선택합니다.

3. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic** 노드를 선택한 후 합니다 **확장성** 노드.

    > [!NOTE]
    > 합니다 **확장성** 노드는 Visual Studio SDK를 설치 하는 경우에 사용할 수 있습니다. 자세한 내용은이 항목 앞부분의 전제 조건 섹션을 참조 하세요.

4. 선택 대화 상자 맨 **.NET Framework 4.5** 버전의.NET Framework의 목록에서입니다.

5. 선택 합니다 **VSIX 프로젝트** 서식 파일을 프로젝트의 이름 **WebPartNode**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **WebPartNode** 프로젝트가 **솔루션 탐색기**합니다.

#### <a name="to-create-the-extension-project"></a>확장 프로젝트를 만들려면

1. **솔루션 탐색기**솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 프로젝트**합니다.

2. 에 **새 프로젝트** 대화 상자에서 합니다 **Visual C#** 노드 또는 **Visual Basic** 노드를 선택한 다음 선택 **Windows** 노드.

3. 선택 대화 상자 맨 **.NET Framework 4.5** 버전의.NET Framework의 목록에서입니다.

4. 프로젝트 템플릿 목록에서 선택 **클래스 라이브러리**, 프로젝트 이름을 **WebPartNodeExtension**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **WebPartNodeExtension** 솔루션에 프로젝트를 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

#### <a name="to-create-the-sharepoint-commands-project"></a>SharePoint 명령은 프로젝트를 만들려면

1. **솔루션 탐색기**솔루션 노드의 바로 가기 메뉴를 열고 **추가**를 선택한 후 **새 프로젝트**합니다.

2. 에 **새 프로젝트** 대화 상자에서 **Visual C#** 노드 또는 **Visual Basic** 노드를 선택한 후의 **Windows** 노드.

3. 선택 대화 상자 맨 **.NET Framework 3.5** 버전의.NET Framework의 목록에서입니다.

4. 프로젝트 템플릿 목록에서 선택 **클래스 라이브러리**, 프로젝트 이름을 **WebPartCommands**를 선택한 후는 **확인** 단추입니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 추가 된 **WebPartCommands** 솔루션에 프로젝트를 기본 Class1 코드 파일을 엽니다.

5. 프로젝트에서 Class1 코드 파일을 삭제 합니다.

## <a name="configure-the-projects"></a>프로젝트 구성
 확장을 만드는 데는 코드를 작성 하기 전에 코드 파일 및 어셈블리 참조를 추가 하 고 프로젝트 설정을 구성 해야 합니다.

#### <a name="to-configure-the-webpartnodeextension-project"></a>WebPartNodeExtension 프로젝트를 구성 하려면

1. WebPartNodeExtension 프로젝트에서 다음 이름을 포함 하는 4 개의 코드 파일을 추가 합니다.

    - SiteNodeExtension

    - WebPartNodeTypeProvider

    - WebPartNodeInfo

    - WebPartCommandIds

2. 바로 가기 메뉴를 열고 합니다 **WebPartNodeExtension** 프로젝트를 선택한 후 **참조 추가**합니다.

3. 에 **참조 관리자-WebPartNodeExtension** 대화 상자를 선택 합니다 **Framework** 탭을 선택한 다음 각 다음 어셈블리에 대 한 확인란을 선택:

    - System.ComponentModel.Composition

    - System.Windows.Forms

4. 선택 합니다 **확장** 탭 Microsoft.VisualStudio.SharePoint 어셈블리에 대 한 확인란을 선택 하 고 다음을 선택 합니다 **확인** 단추.

5. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **WebPartNodeExtension** 프로젝트 노드를 선택한 후 **속성**합니다.

     **프로젝트 디자이너**가 열립니다.

6. **애플리케이션** 탭을 선택합니다.

7. 에 **기본 네임 스페이스** 상자 (C#) 또는 **루트 네임 스페이스** 상자 ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), 입력 **ServerExplorer.SharePointConnections.WebPartNode**합니다.

#### <a name="to-configure-the-webpartcommands-project"></a>Webpartcommands 프로젝트를 구성 하려면

1. WebPartCommands 프로젝트에서 WebPartCommands 이라고 하는 코드 파일을 추가 합니다.

2. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **WebPartCommands** 프로젝트 노드를 선택 **추가**를 선택한 후 **기존 항목**.

3. 에 **기존 항목 추가** 대화 상자에서 WebPartNodeExtension 프로젝트에 대 한 코드 파일이 포함 된 폴더로 이동 하 고 WebPartNodeInfo 및 WebPartCommandIds 코드 파일을 선택 합니다.

4. 옆의 화살표를 선택 합니다 **추가** 단추를 선택한 후 **링크로 추가** 나타나는 메뉴에서.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 코드 파일을 링크로 WebPartCommands 프로젝트에 추가합니다. 결과적으로, WebPartNodeExtension 프로젝트에서 코드 파일은 있지만 파일의 코드 WebPartCommands 프로젝트에서 파일도 컴파일됩니다.

5. 바로 가기 메뉴를 열고 합니다 **WebPartCommands** 프로젝트를 다시 선택한 **참조 추가**합니다.

6. 에 **참조 관리자-WebPartCommands** 대화 상자를 선택 합니다 **확장** 탭, 각 다음 어셈블리에 대 한 확인란을 선택 하 고 선택한를 **확인** 단추:

    - Microsoft.SharePoint

    - Microsoft.VisualStudio.SharePoint.Commands

7. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **WebPartCommands** 다시 프로젝트를 선택한 다음 **속성**합니다.

     **프로젝트 디자이너**가 열립니다.

8. **애플리케이션** 탭을 선택합니다.

9. 에 **기본 네임 스페이스** 상자 (C#) 또는 **루트 네임 스페이스** 상자 ([!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]), 입력 **ServerExplorer.SharePointConnections.WebPartNode**합니다.

## <a name="create-icons-for-the-new-nodes"></a>새 노드에 대 한 아이콘 만들기
 에 대 한 두 아이콘을 만듭니다는 **서버 탐색기** 확장: 새 아이콘 **웹 파트 갤러리** 노드와 아래 자식 웹 파트 노드마다 다른 아이콘은 **웹 파트 갤러리** 노드입니다. 이 연습의 뒷부분에서는 노드를 사용 하 여 이러한 아이콘을 연결 하는 코드를 작성 합니다.

#### <a name="to-create-icons-for-the-nodes"></a>노드에 대 한 아이콘을 만들려면

1. **솔루션 탐색기**에 대 한 바로 가기 메뉴를 열고 합니다 **WebPartNodeExtension** 프로젝트를 선택한 후 **속성**합니다.

2. **프로젝트 디자이너**가 열립니다.

3. 선택 된 **리소스** 탭을 선택한 후는 **이 프로젝트에 기본 리소스 파일이 없습니다. 만들려면 여기를 클릭 하십시오.** 링크 합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 리소스 파일을 만들고 디자이너에서 열립니다.

4. 디자이너의 맨 위에 있는 화살표를 옆에 선택 합니다 **리소스 추가** 메뉴 명령을 선택한 후 **새 아이콘 추가** 나타나는 메뉴에서.

5. 에 **새 리소스 추가** 대화 상자에서 이름 새로 만들기 아이콘 **WebPartsNode**를 선택한 후는 **추가** 단추입니다.

     새 아이콘의 엽니다는 **이미지 편집기**합니다.

6. 쉽게 인식할 수 있는 디자인을 갖도록 아이콘의 16 x 16 버전을 편집 합니다.

7. 아이콘을 32 x 32 버전에 대 한 바로 가기 메뉴를 열고 선택한 **이미지 형식 삭제**합니다.

8. 프로젝트 리소스에 두 번째 아이콘을 추가 하려면 5-8 단계를 반복 하 고이 아이콘을 이름을 **WebPart**합니다.

9. **솔루션 탐색기**아래에 있는 합니다 **리소스** 폴더를 **WebPartNodeExtension** 프로젝트, 바로 가기 메뉴를 열고 **WebPartsNode.ico**.

10. 에 **속성** 창 옆에 화살표를 선택 **빌드 작업**를 선택한 후 **포함 리소스** 나타나는 메뉴에서.

11. 에 대 한 마지막 두 단계를 반복 **WebPart.ico**합니다.

## <a name="add-the-web-part-gallery-node-to-server-explorer"></a>서버 탐색기에 웹 파트 갤러리 노드 추가
 새 추가 하는 클래스를 만듭니다 **웹 파트 갤러리** 각 SharePoint 사이트 노드가 노드. 클래스를 구현 하는 새 노드를 추가 하 여 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> 인터페이스입니다. 기존 노드의 동작을 확장 하려고 할 때마다이 인터페이스를 구현 **서버 탐색기**, 노드를 자식 노드를 추가 하는 등입니다.

#### <a name="to-add-the-web-part-gallery-node-to-server-explorer"></a>서버 탐색기에 웹 파트 갤러리 노드를 추가 하려면

1. WebPartNodeExtension 프로젝트에서 SiteNodeExtension 코드 파일을 열고 다음 코드를 붙여 넣습니다.

    > [!NOTE]
    > 이 코드를 추가, 프로젝트를 컴파일 오류가 발생 해야 합니다. 해당 위치로 이동 후 추가 하면 코드 이후 단계에서.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/sitenodeextension.cs#1)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#1](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/sitenodeextension.vb#1)]

## <a name="define-a-node-type-that-represents-a-web-part"></a>웹 파트를 나타내는 노드 형식을 정의 합니다.
 새로운 유형의 웹 파트를 나타내는 노드를 정의 하는 클래스를 만듭니다. Visual Studio는 아래에 자식 노드를 표시 하려면이 새 노드 형식을 사용 합니다 **웹 파트 갤러리** 노드. 각 자식 노드에 SharePoint 사이트에 단일 웹 파트를 나타냅니다.

 클래스를 구현 하는 새 노드 형식을 정의 하는 <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider> 인터페이스입니다. 에 있는 노드의 새 형식을 정의 하려고 할 때마다이 인터페이스를 구현 **서버 탐색기**합니다.

#### <a name="to-define-the-web-part-node-type"></a>웹 파트 노드 형식을 정의 하려면

1. WebPartNodeExtension 프로젝트에서 WebPartNodeTypeProvder 코드 파일을 열고 다음 코드를 붙여 넣습니다.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodetypeprovider.vb#2)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#2](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodetypeprovider.cs#2)]

## <a name="define-the-web-part-data-class"></a>웹 파트 데이터 클래스를 정의 합니다.
 SharePoint 사이트의 단일 웹 파트에 대 한 데이터를 포함 하는 클래스를 정의 합니다. 이 연습의 뒷부분에서는 사이트에서 각 웹 파트에 대 한 데이터를 검색 한 다음이 클래스의 인스턴스에 데이터를 할당 하는 사용자 지정 SharePoint 명령을 만들게 됩니다.

#### <a name="to-define-the-web-part-data-class"></a>웹 파트 데이터 클래스를 정의 하려면

1. WebPartNodeExtension 프로젝트에서 WebPartNodeInfo 코드 파일을 열고 다음 코드를 붙여 넣습니다.

     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartnodeinfo.vb#3)]
     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#3](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartnodeinfo.cs#3)]

## <a name="define-the-ids-for-the-sharepoint-commands"></a>SharePoint 명령에 대 한 Id를 정의 합니다.
 사용자 지정 SharePoint 명령을 식별 하는 여러 문자열을 정의 합니다. 이 연습의 뒷부분에서 이러한 명령을 구현 합니다.

#### <a name="to-define-the-command-ids"></a>명령 Id를 정의 하려면

1. WebPartNodeExtension 프로젝트에서 WebPartCommandIds 코드 파일을 열고 다음 코드를 붙여 넣습니다.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/CSharp/WebPartNode/webpartnodeextension/webpartcommandids.cs#4)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#4](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartnodeextension/webpartcommandids.vb#4)]

## <a name="create-the-custom-sharepoint-commands"></a>사용자 지정 SharePoint 명령 만들기
 SharePoint 사이트에서 웹 파트에 대 한 데이터를 검색 하는 SharePoint에 대 한 서버 개체 모델을 호출 하는 사용자 지정 명령을 만듭니다. 각 명령은 변수가 있는 메서드에 <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> 적용 합니다.

#### <a name="to-define-the-sharepoint-commands"></a>SharePoint를 정의 하는 명령

1. WebPartCommands 프로젝트에서 WebPartCommands 코드 파일을 열고 다음 코드를 붙여 넣습니다.

     [!code-csharp[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/CSharp/WebPartNode/WebPartCommands/WebPartCommands.cs#6)]
     [!code-vb[SPExtensibility.SPExplorer.WebPartNodeWithCommands#6](../sharepoint/codesnippet/VisualBasic/spextensibility.spexplorer.webpartnodewithcommands.webpartnode/webpartcommands/webpartcommands.vb#6)]

## <a name="checkpoint"></a>검사점
 이 시점에서 연습에서는 모든 코드를 **웹 파트 갤러리** 노드와 SharePoint 명령은 현재 위치는 프로젝트. 두 프로젝트가 오류 없이 컴파일는 되도록 솔루션을 빌드하십시오.

#### <a name="to-build-the-solution"></a>솔루션을 빌드하려면

1. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

    > [!WARNING]
    > 이 시점에서 WebPartNode 프로젝트는 VSIX 매니페스트 파일 작성자에 대 한 값이 없는 때문에 빌드 오류가 있을 수 있습니다. 이 오류는 사라집니다 이후 단계에서 값을 추가 합니다.

## <a name="create-a-vsix-package-to-deploy-the-extension"></a>확장을 배포 하는 VSIX 패키지 만들기
 확장을 배포 하려면 솔루션에서 VSIX 프로젝트를 사용 하 여 VSIX 패키지를 만듭니다. VSIX 프로젝트에서 source.extension.vsixmanifest 파일을 수정 하 여 VSIX 패키지를 먼저 구성 합니다. 그런 다음 솔루션을 구축 하 여 VSIX 패키지를 만듭니다.

#### <a name="to-configure-the-vsix-package"></a>VSIX 패키지를 구성 하려면

1. **솔루션 탐색기**, WebPartNode 프로젝트에서 열을 **source.extension.vsixmanifest** 매니페스트 편집기에서 파일.

     Source.extension.vsixmanifest 파일에는 모든 VSIX 패키지 해야 하는 extension.vsixmanifest 파일에 대 한 기반이 됩니다. 이 파일에 대 한 자세한 내용은 참조 하세요. [VSIX 확장 스키마 1.0 참조](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)합니다.

2. 에 **Product Name** 상자에 입력 합니다 **서버 탐색기에 대 한 웹 파트 갤러리 노드**합니다.

3. 에 **작성자** 상자에 입력 합니다 **Contoso**합니다.

4. 에 **설명을** 상자에 입력 **사용자 지정 웹 파트 갤러리 노드 서버 탐색기에서 SharePoint 연결 노드를 추가 합니다. 이 확장을 사용자 지정 SharePoint 명령을 사용 하 여 서버 개체 모델을 호출 합니다.**

5. 선택는 **자산** 편집기의 탭을 선택 하 고는 **새로 만들기** 단추.

     합니다 **새 자산 추가** 대화 상자가 나타납니다.

6. 에 **형식** 목록에서 선택 **Microsoft.VisualStudio.MefComponent**합니다.

    > [!NOTE]
    > 이 값에 해당 하는 `MefComponent` extension.vsixmanifest 파일의 요소입니다. 이 요소는 VSIX 패키지 확장 어셈블리의 이름을 지정합니다. 자세한 내용은 [MEFComponent 요소 (VSX 스키마)](/previous-versions/visualstudio/visual-studio-2010/dd393736\(v\=vs.100\))합니다.

7. 에 **소스** 목록에서 선택 **현재 솔루션의 프로젝트**합니다.

8. 에 **프로젝트** 목록에서 선택 **WebPartNodeExtension** 를 선택한 후는 **확인** 단추입니다.

9. 매니페스트 편집기에서 선택 합니다 **새로 만들기** 단추를 다시 합니다.

     합니다 **새 자산 추가** 대화 상자가 나타납니다.

10. 에 **형식** 상자에 입력 합니다 **SharePoint.Commands.v4**합니다.

    > [!NOTE]
    > 이 요소는 Visual Studio 확장에 포함 하려는 사용자 지정 확장을 지정 합니다. 자세한 내용은 [자산 요소 (VSX 스키마)](https://msdn.microsoft.com/9fcfc098-edc7-484b-9d4c-acd17829d737)합니다.

11. 에 **원본** 목록에서 선택 합니다 **현재 솔루션의 프로젝트** 목록 항목입니다.

12. 에 **프로젝트** 목록에서 선택 **WebPartCommands**를 선택한 후는 **확인** 단추입니다.

13. 메뉴 모음에서 **빌드합니다** > **솔루션 빌드**, 솔루션이 오류 없이 컴파일되는지 확인 한 후 확인 합니다.

14. WebPartNode 프로젝트의 빌드 출력 폴더에 이제 WebPartNode.vsix 파일을 포함 해야 합니다.

     빌드 출력 폴더는 기본적으로... 프로젝트 파일이 포함 된 폴더 아래에 있는 \bin\Debug 폴더입니다.

## <a name="test-the-extension"></a>테스트 확장
 이제 새 테스트 준비가 **웹 파트 갤러리** 노드에서 **서버 탐색기**합니다. 먼저 Visual Studio의 실험적 인스턴스에서 확장 디버깅을 시작 합니다. 를 사용 하 여 새 **웹 파트** 실험적 인스턴스의 노드 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]합니다.

#### <a name="to-start-debugging-the-extension"></a>디버깅 확장을 시작 하려면

1. 다시 시작 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 관리자 자격 증명과 WebPartNode 솔루션을 엽니다.

2. WebPartNodeExtension 프로젝트에서 SiteNodeExtension 코드 파일을 열고 다음 코드의 첫 번째 줄에 중단점을 추가 합니다 `NodeChildrenRequested` 고 `CreateWebPartNodes` 메서드.

3. 선택 된 **F5** 디버깅을 시작 하는 키입니다.

     Visual Studio 서버 Explorer\1.0에 대 한 %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0Exp\Extensions\Contoso\Web 파트 갤러리 노드 확장에 확장이 설치 되 고 Visual Studio의 실험적 인스턴스를 시작 합니다. Visual Studio의이 인스턴스에 있는 프로젝트 항목을 테스트 합니다.

#### <a name="to-test-the-extension"></a>확장을 테스트 하려면

1. 실험적 인스턴스에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 메뉴 모음에서 **보기** > **서버 탐색기**합니다.

2. 테스트에 사용 하려는 SharePoint 사이트에서 표시 되지 않으면 다음 단계를 수행 합니다 **SharePoint 연결** 노드에서 **서버 탐색기**:

    1. **서버 탐색기**에 대 한 바로 가기 메뉴를 열고 **SharePoint 연결**를 선택한 후 **연결 추가**합니다.

    2. 에 **SharePoint 연결 추가** 대화 상자에 연결 하 고 선택 하려는 SharePoint 사이트에 대 한 URL을 입력 합니다 **확인** 단추.

         개발 컴퓨터에 SharePoint 사이트를 지정 하려면 입력 **http://localhost** 합니다.

3. (표시 하는 사이트의 URL) 사이트 연결 노드를 확장 하 고를 자식 사이트 노드를 확장 (예를 들어 **팀 사이트**).

4. 확인 코드의 다른 인스턴스에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서 이전에 설정한 중단점에서 중지를 `NodeChildrenRequested` 메서드를 선택한 후 **F5** 계속 프로젝트를 디버그 하려면.

5. Visual Studio의 실험적 인스턴스에서 확인 이라는 새 노드가 **웹 파트 갤러리** 최상위 사이트 노드 아래에 표시 한 다음를 확장 합니다 **웹 파트 갤러리** 노드.

6. 다른 인스턴스의 Visual Studio의 코드에서 이전에 설정한 중단점에서 중지 확인 합니다 `CreateWebPartNodes` 메서드를 선택한 후 합니다 **F5** 계속 프로젝트를 디버그 하려면 키.

7. Visual Studio의 실험적 인스턴스에서 연결된 된 사이트의 모든 웹 파트가 나타나는지 확인 합니다 **웹 파트 갤러리** 노드에서 **서버 탐색기**합니다.

8. **서버 탐색기**, 웹 파트 중 하나에 대 한 바로 가기 메뉴를 열고 선택한 후 **속성**합니다.

9. 인스턴스에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디버그 하는, 웹 파트에 대 한 세부 정보에 표시 되는지 확인 합니다 **속성** 창.

## <a name="uninstall-the-extension-from-visual-studio"></a>Visual Studio에서 확장을 제거 합니다.
 확장 테스트를 마친 후 Visual Studio에서 확장을 제거 합니다.

#### <a name="to-uninstall-the-extension"></a>확장을 제거하려면

1. 실험적 인스턴스에서 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], 메뉴 모음에서 **도구** > **확장 및 업데이트**합니다.

     **확장명 및 업데이트** 대화 상자가 열립니다.

2. 확장의 목록에서 선택 **서버 탐색기에 대 한 웹 파트 갤러리 노드 확장**를 선택한 후 합니다 **제거** 단추입니다.

3. 나타나는 대화 상자에서 선택 합니다 **예** 확장을 제거 하 여 선택한 것을 확인 하려면 단추를 **지금 다시 시작** 제거를 완료 하려면 단추입니다.

4. Visual Studio (실험적 인스턴스 및 WebPartNode 솔루션이 열려 있는 Visual Studio의 인스턴스)의 두 인스턴스를 닫습니다.

## <a name="see-also"></a>참고자료
- [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [연습: 서버 탐색기 확장의 SharePoint 클라이언트 개체 모델 호출](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)
- [아이콘에 대한 이미지 편집기](/cpp/windows/image-editor-for-icons)
- [아이콘 또는 다른 이미지 만들기 &#40;아이콘에 대 한 이미지 편집기&#41;](/cpp/windows/creating-an-icon-or-other-image-image-editor-for-icons)
