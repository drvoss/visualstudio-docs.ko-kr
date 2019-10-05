---
title: SharePoint의 프로그래밍 모델 개요 도구 확장
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dbb496b077f1ff55fda53d3325765e8e58911096
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401777"
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>SharePoint의 프로그래밍 모델 개요 도구 확장
  Visual Studio에서 SharePoint 도구의 확장을 만드는 경우 SharePoint 도구에서 노출하는 확장성 인터페이스를 하나 이상 구현하여 시작합니다. 대부분의 경우 SharePoint 도구에서 제공하는 다른 형식을 사용하여 확장에서 기능도 구현합니다. 일부 시나리오에서는 Visual Studio 및 SharePoint에서 제공하는 다른 개체 모델의 형식을 사용할 수도 있습니다. 각 개체 모델의 용도 이해 하 고 SharePoint 도구의 확장을 만들려면 서로 사용 하는 방법을 알고 있어야 합니다.

## <a name="extend-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>확장성 인터페이스를 구현 하 여 SharePoint 도구 확장
 Visual Studio에서는 .NET Framework 4의 MEF(Managed Extensibility Framework)를 사용하여 SharePoint 도구에 대한 확장성 모델을 제공합니다. MEF는 System.ComponentModel.Composition 어셈블리에서 구현된 API로, 애플리케이션에서 확장성 지점을 노출하고 런타임에 확장을 검색하고 로드할 수 있도록 합니다. MEF에 대 한 자세한 내용은 참조 하세요. [Managed Extensibility Framework &#40;MEF&#41;](/dotnet/framework/mef/index)합니다.

 SharePoint 도구를 확장하려면 Visual Studio에서 노출하는 확장성 인터페이스를 하나 이상 구현합니다. 또한 <xref:System.ComponentModel.Composition.ExportAttribute>와 필요에 따라 추가 SharePoint 도구 관련 특성을 인터페이스 구현에 적용해야 합니다. 다음 표에는 SharePoint 도구를 확장하기 위해 구현할 수 있는 인터페이스가 나와 있습니다.

|인터페이스|설명|
|---------------|-----------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|새 형식의 SharePoint 프로젝트 항목을 정의하려면 이 인터페이스를 구현합니다. 예는 [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|Visual Studio에 이미 설치되어 있는 SharePoint 프로젝트 항목의 형식을 확장하려면 이 인터페이스를 구현합니다. 예는 [방법: SharePoint 프로젝트 항목 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|SharePoint 프로젝트를 확장하려면 이 인터페이스를 구현합니다. 예는 [방법: SharePoint 프로젝트 확장명 만들기](../sharepoint/how-to-create-a-sharepoint-project-extension.md)합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|SharePoint 프로젝트 항목이 배포되거나 취소될 때 실행할 수 있는 새로운 배포 단계를 정의하려면 이 인터페이스를 구현합니다. 예제를 보려면 [연습: SharePoint 프로젝트용 사용자 지정 배포 단계 만들기](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|기존 노드를 확장 하려면이 인터페이스를 구현 합니다 **SharePoint 연결** 에서 노드를 **서버 탐색기** 창입니다. 예는 [방법: 서버 탐색기에서 SharePoint 노드 확장](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|노드에서 새 형식을 정의 하려면이 인터페이스를 구현 합니다 **SharePoint 연결** 에서 노드를 **서버 탐색기** 창입니다. 예는 [방법: 서버 탐색기에서 SharePoint 노드 확장](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|사용자 지정 기능 유효성 검사 규칙을 정의하려면 이 인터페이스를 구현합니다. 예는 [방법: SharePoint 솔루션에 대 한 유효성 검사 규칙 사용자 지정 기능 및 패키지를 만들](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|사용자 지정 패키지 유효성 검사 규칙을 정의하려면 이 인터페이스를 구현합니다. 예는 [방법: SharePoint 솔루션에 대 한 유효성 검사 규칙 사용자 지정 기능 및 패키지를 만들](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)합니다.|

 SharePoint 도구의 확장을 구현한 후에는 VSIX(Visual Studio Extension) 패키지의 확장 어셈블리를 배포하여 Visual Studio에서 확장을 검색하고 로드할 수 있도록 합니다. 자세한 내용은 [Visual Studio에서 SharePoint 도구의 확장을 배포할](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)합니다.

## <a name="understand-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>SharePoint 도구 확장에서 사용 하는 개체 모델 이해
 SharePoint 도구의 확장을 만들 때 사용할 수 있는 몇 가지 개체 모델은 다음과 같습니다.

- *SharePoint 도구 개체 모델*합니다. 이 개체 모델에서는 SharePoint 도구 확장과 기타 관련 형식을 만들기 위해 구현하는 확장성 인터페이스를 제공합니다.

- *Visual Studio 자동화 및 통합 개체 모델*합니다. 이러한 개체 모델을 사용하여 SharePoint 도구 개체 모델의 범위를 벗어나는 Visual Studio 기능에 액세스할 수 있습니다.

    > [!NOTE]
    > SharePoint 프로젝트 서비스를 사용하여 SharePoint 도구 개체 모델의 일부 개체를 Visual Studio 자동화 및 통합 개체 모델의 개체로 변환하거나 그 반대로 변환할 수 있습니다. 자세한 내용은 [SharePoint 프로젝트 시스템 형식과 기타 Visual Studio 프로젝트 형식 간의 변환](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)합니다.

- *SharePoint 서버 및 클라이언트 개체 모델*합니다. 이러한 개체 모델을 사용하여 SharePoint 사이트를 수정하여 SharePoint 도구 확장의 컨텍스트에서 SharePoint 사이트의 데이터를 검색할 수 있습니다.

### <a name="sharepoint-tools-object-model"></a>SharePoint 도구 개체 모델
 각 SharePoint 도구 확장에서는 SharePoint 도구 개체 모델의 형식을 사용하여 확장의 핵심 동작 및 기능을 정의합니다. 다음 표에서 포함 된 어셈블리에서이 개체 모델에 포함 된 네임 스페이스를 설명 합니다.

#### <a name="microsoftvisualstudiosharepointdll"></a>Microsoft.VisualStudio.SharePoint.dll

|네임스페이스|설명|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint>|SharePoint 프로젝트 시스템을 확장하고 자동화하는 데 사용하는 형식을 포함합니다. 예를 들어 기본 제공 SharePoint 프로젝트 및 프로젝트 항목을 확장하거나, 고유한 프로젝트 항목을 만들 수 있습니다. 자세한 내용은 [SharePoint 프로젝트 시스템 확장](../sharepoint/extending-the-sharepoint-project-system.md)합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.Deployment>|사용자 고유의 배포 단계 및 배포 구성을 만드는 등 SharePoint 프로젝트에 대한 배포 프로세스를 확장하는 데 사용하는 형식을 포함합니다. 자세한 내용은 [확장 SharePoint 패키징 및 배포](../sharepoint/extending-sharepoint-packaging-and-deployment.md)합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer>|아래에 있는 노드를 확장 하는 데 사용 하는 형식을 포함 합니다 **SharePoint 연결** 에서 노드를 **서버 탐색기** 창 새로운 형식의 노드를 정의할 수입니다. 자세한 내용은 [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.Features>|SharePoint 프로젝트의 기능 정의에 액세스하는 데 사용되는 형식을 포함합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.Packages>|SharePoint 솔루션의 패키지 정의에 액세스하는 데 사용되는 형식을 포함합니다.|
|<xref:Microsoft.VisualStudio.SharePoint.Validation>|SharePoint 프로젝트의 기능 및 패키지 유효성 검사 동작을 사용자 지정하는 데 사용되는 형식을 포함합니다. 자세한 내용은 [방법: SharePoint 솔루션에 대 한 유효성 검사 규칙 사용자 지정 기능 및 패키지를 만들](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)합니다.|

#### <a name="microsoftvisualstudiosharepointcommandsdll"></a>Microsoft.VisualStudio.SharePoint.Commands.dll

|네임스페이스|설명|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Commands>|사용자 지정을 만드는 데 사용할 수 있는 형식을 포함 *SharePoint 명령을*합니다. SharePoint 명령은 SharePoint 도구 확장에서 SharePoint 서버 개체 모델을 호출하는 메서드입니다. 자세한 내용은 [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)합니다.|

#### <a name="microsoftvisualstudiosharepointexplorerextensionsdll"></a>Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll

|네임스페이스|설명|
|-|-|
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|기본 제공에 대 한 정보를 가져오는 데 사용할 수 있는 형식을 포함 **서버 탐색기** 목록, 필드 또는 콘텐츠 형식을 나타내는 노드 같은 SharePoint 사이트에서 개별 구성 요소를 나타내는 노드. 자세한 내용은 [서버 탐색기에서 SharePoint 연결 노드 확장](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)합니다.|

### <a name="visual-studio-automation-object-model"></a>Visual Studio 자동화 개체 모델
 Visual Studio 자동화 개체 모델은 Visual Studio 프로젝트와 IDE를 자동화하는 데 사용할 수 있는 API를 제공합니다. Visual Studio 개체 모델을 사용하면 SharePoint 프로젝트에 한정되지 않는 프로젝트 관련 작업을 수행하거나 Visual Studio에서 기타 일반적인 자동화 작업을 수행할 수 있습니다. 이 개체 모델은 일반적으로 Visual Studio 추가 기능 및 매크로에 많이 사용하지만 Sharepoint 도구 확장에 사용할 수도 있습니다.

 Visual Studio 자동화 개체 모델의 주요 부분에 정의 된 *EnvDTE.dll* 어셈블리입니다. 합니다 *EnvDTE\\\<버전 >.dll* 어셈블리는 특정 버전의 Visual Studio에 도입 된 추가 기능을 제공 합니다. Visual Studio에 포함되어 있습니다.

 자동화 개체 모델에 대 한 자세한 내용은 참조 하세요. [Visual Studio SDK 참조](../extensibility/visual-studio-sdk-reference.md)합니다.

### <a name="visual-studio-integration-object-model"></a>Visual Studio 통합 개체 모델
 통합 개체 모델을 만들어 Visual Studio에 기능을 추가 하는 데 사용할 수 있는 Api를 제공 된 *VSPackage*합니다. VSPackage는 도구 창, 편집기, 디자이너, 서비스, 프로젝트 등의 사용자 지정 기능을 제공하여 Visual Studio IDE를 확장하는 모듈입니다.

 기본 제공 SharePoint 도구와 함께 사용할 새 Visual Studio 기능을 추가하려는 경우 통합 개체 모델을 사용할 수 있습니다. 예를 들어 SharePoint 사이트에 대한 사용자 지정 작업을 나타내는 사용자 지정 SharePoint 프로젝트 항목을 만드는 경우 사용자 지정 작업용 디자이너를 구현하는 VSPackage를 만들 수도 있습니다. 사용자 지정 작업을 나타내는 프로젝트 항목에 바로 가기 메뉴 항목을 추가 하 여 사용자 지정 작업을 사용 하 여 디자이너를 연결할 수 있습니다 **솔루션 탐색기**합니다. 바로 가기 메뉴를 열어 디자이너를 열 수 있습니다 (사용자 지정 작업 프로젝트 항목을 마우스 오른쪽 단추로 클릭 하거나 선택한 다음,이 선택 하 여 합니다 **Shift**+**F10** 키)를 선택한 다음 **열려**합니다.

 이 개체 모델은 Visual Studio SDK에 포함된 어셈블리 집합에서 정의됩니다. 이 개체 모델의 주 어셈블리의 일부를 포함 *Microsoft.VisualStudio.Shell.11.0.dll*하십시오 *Microsoft.VisualStudio.Shell.Interop.dll*, 및  *Microsoft.VisualStudio.OLE.Interop.dll*합니다.

 통합 개체 모델에 대 한 자세한 내용은 참조 하세요. [자동화 모델 개요](../extensibility/internals/automation-model-overview.md) 하 고 [Visual Studio SDK 참조](../extensibility/visual-studio-sdk-reference.md)합니다.

### <a name="sharepoint-object-models"></a>SharePoint 개체 모델
 SharePoint 도구 확장에서는 SharePoint API를 사용하여 SharePoint 사이트를 수정하거나 SharePoint 사이트에서 데이터를 검색할 수 있습니다. [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 및 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]에서는 두 가지 개체 모델인 서버 개체 모델과 클라이언트 개체 모델을 제공합니다.

 SharePoint 도구 확장에서 두 개체 모델의 API를 모두 사용할 수 있지만 SharePoint 도구 확장의 컨텍스트에서 각 개체 모델에 장단점이 있습니다. 자세한 내용은 [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)합니다.

|개체 모델|설명|
|------------------|-----------------|
|서버 개체 모델|서버 개체 모델을 사용하면 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 및 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)]에 표시되는 모든 기능을 프로그래밍 방식으로 액세스할 수 있습니다. 이 개체 모델은 SharePoint 서버에서 실행되는 SharePoint 솔루션에 사용됩니다. 이 개체 모델의 대부분에 정의 되어는 *Microsoft.SharePoint.dll* 어셈블리입니다. 서버 개체 모델에 대 한 자세한 내용은 참조 하세요. [SharePoint Foundation Server 쪽 개체 모델을 사용 하 여](http://go.microsoft.com/fwlink/?LinkId=177796)입니다.|
|클라이언트 개체 모델|클라이언트 개체 모델은 원격 클라이언트나 서버의 SharePoint 데이터와 상호 작용하는 데 사용할 수 있는 서버 개체 모델의 하위 집합입니다. 이 모델은 일반적인 작업을 수행하기 위해 실행해야 하는 왕복 수를 최소화하도록 디자인되었습니다. 대부분의 클라이언트 개체 모델에 정의 되어는 *대부분 Microsoft.SharePoint.Client.dll* 하 고 *Microsoft.SharePoint.Client.Runtime.dll* 어셈블리입니다. 클라이언트 개체 모델에 대 한 자세한 내용은 참조 하세요. [관리 클라이언트 개체 모델](http://go.microsoft.com/fwlink/?LinkId=177797)합니다.|

## <a name="see-also"></a>참고자료
- [Visual Studio에서 SharePoint 도구 확장](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [SharePoint 개체 모델 호출](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [SharePoint 프로젝트 서비스 사용](../sharepoint/using-the-sharepoint-project-service.md)
