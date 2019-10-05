---
title: 서버 탐색기에서 기본 제공 SharePoint 노드에 대 한 데이터 가져오기
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b90582c9b8d352f95d3d5abb3bbb7fb69283b06b
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401411"
---
# <a name="how-to-get-data-for-a-built-in-sharepoint-node-in-server-explorer"></a>방법: 서버 탐색기에서 기본 제공 SharePoint 노드에 대 한 데이터 가져오기
  각 기본 제공 SharePoint 노드에 대 한 **서버 탐색기**, 노드에서 나타내는 기본 SharePoint 구성 요소에 대 한 데이터를 가져올 수 있습니다. 자세한 내용은 [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)합니다.

## <a name="example"></a>예제
 다음 코드 예제에는 목록 노드를 나타내는 기본 SharePoint 목록에 대 한 데이터를 가져오는 방법을 보여 줍니다 **서버 탐색기**합니다. 기본적으로 노드 목록에는 **브라우저에서 보기** 목록을 웹 브라우저에서 열기 위해 클릭할 수 있는 상황에 맞는 메뉴 항목입니다. 추가 하 여 목록 노드를 확장 하는이 예제는 **Visual Studio에서 보기** 목록은 Visual Studio에서 직접 열리는 상황에 맞는 메뉴 항목입니다. Visual Studio에서 열 목록의 URL을 가져오려면 노드에 대 한 목록 데이터를 액세스 하는 코드입니다.

 [!code-vb[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextensionnodeinfo.vb#10)]
 [!code-csharp[SPExtensibility.ProjectSystemExtension.General#10](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextensionnodeinfo.cs#10)]

 SharePoint 프로젝트 서비스를 사용 하 여 가져오려고는이 예제는 <xref:EnvDTE.DTE> Visual Studio에서 여는 데 사용 되는 개체를 나열 합니다. SharePoint 프로젝트 서비스에 대 한 자세한 내용은 참조 하세요. [SharePoint 프로젝트 서비스를 사용 하 여](../sharepoint/using-the-sharepoint-project-service.md)입니다.

 SharePoint 노드 확장을 만드는 기본 작업에 대 한 자세한 내용은 참조 하세요. [방법: 서버 탐색기에서 SharePoint 노드 확장](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)합니다.

## <a name="compile-the-code"></a>코드 컴파일
 이 예제에는 다음 어셈블리에 대 한 참조가 필요합니다.

- EnvDTE

- Microsoft.VisualStudio.SharePoint

- Microsoft.VisualStudio.SharePoint.Explorer.Extensions

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>확장 배포
 배포 하는 **서버 탐색기** 확장을 만들기를 [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] 어셈블리 및 확장을 사용 하 여 배포 하려는 다른 파일에 대 한 패키지 (VSIX) 확장 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구의 확장을 배포할](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="see-also"></a>참고자료
- [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [방법: 서버 탐색기에서 SharePoint 노드 확장](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)
- [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)
- [Visual Studio에서 SharePoint 도구에 대 한 확장 배포](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
