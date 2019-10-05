---
title: ProjectItem 요소 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2768a2e55b3e38158f2ef6b856a653a1a2c12dfa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562405"
---
# <a name="projectitem-element"></a>ProjectItem 요소
  SharePoint 프로젝트 항목을 나타냅니다. 이 요소는 필수 루트 요소에는 *.spdata* 파일.

## <a name="syntax"></a>구문

```xml
<ProjectItem DefaultFile = "File that opens in the editor when you open the project item"
    FeatureReceiverClass = "Class that implements a feature receiver for the project item"
    FeatureReceiverAssembly = "Assembly that defines a feature receiver for the project item"
    SupportedTrustLevels = "Trust levels that the project item supports"
    SupportedDeploymentScopes = "Deployment scopes that the project item supports"
    Type="Identifier for the project item">
  <Files>...</Files>
  <ProjectItemFolder>...</ProjectItemFolder>
  <SafeControls>...</SafeControls>
  <FeatureProperties>...</FeatureProperties>
  <ExtensionData>...</ExtensionData>
</ProjectItem>
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|**DefaultFile**|선택적 **xs: string** 특성입니다.<br /><br /> 상대 경로에 있는 SharePoint 프로젝트 항목을 열 때 Visual Studio 편집기에서 열려 있는 파일의 파일 이름 포함 **솔루션 탐색기**합니다. 경로 포함 된 폴더에서 상대 경로 *.spdata* 파일입니다.|
|**FeatureReceiverClass**|선택적 **xs: string** 특성입니다.<br /><br /> 이 SharePoint 프로젝트 항목에 대 한 기능 수신기 클래스의 정규화 된 이름입니다. 기능 수신기에 대 한 자세한 내용은 참조 하세요. [프로젝트 항목에 패키징 및 배포 정보를 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)합니다.|
|**FeatureReceiverAssembly**|선택적 **xs: string** 특성입니다.<br /><br /> 이 SharePoint 프로젝트 항목에 대 한 기능 수신기를 정의 하는 어셈블리의 정규화 된 이름을 지정 합니다. 기능 수신기에 대 한 자세한 내용은 참조 하세요. [프로젝트 항목에 패키징 및 배포 정보를 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)합니다. 정규화 된 어셈블리 이름에 대 한 자세한 내용은 참조 하세요. [어셈블리 이름](/dotnet/framework/app-domains/assembly-names)합니다.|
|**SupportedTrustLevels**|선택적 **xs: string** 특성입니다.<br /><br /> 이 SharePoint 프로젝트 항목을 지 원하는 신뢰 수준을 지정 합니다. 이 값에는 다음 문자열 중 하나일 수 있습니다. 샌드박스, FullTrust 또는 모든 합니다. 값 All Sandboxed와 FullTrust를 지정 합니다.<br /><br /> 사용자 지정 SharePoint 프로젝트 항목 형식에서이 특성의 값을 할당 하는 값에 해당 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> 구현에서 속성을 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 메서드. Visual Studio에서 지정 하는 동일한 신뢰 수준을 지정 되도록 값을 덮어씁니다이 특성에 대해 다른 값을 지정 하는 경우는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedTrustLevels%2A> 속성입니다.|
|**SupportedDeploymentScopes**|선택적 **xs: string** 특성입니다.<br /><br /> 이 SharePoint 프로젝트 항목을 지 원하는 배포 범위를 지정 합니다. 이 값은 다음 문자열 중 하나 이상의 구성 된 쉼표로 구분 된 문자열: 팜, 사이트, 웹, 웹 응용 프로그램 또는 패키지 있습니다. 예를 들면 다음과 같습니다: `Web, Site`<br /><br /> 사용자 지정 SharePoint 프로젝트 항목 형식에서이 특성의 값을 할당 하는 값에 해당 합니다 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> 구현에서 속성을 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> 메서드. Visual Studio에서 지정 하는 동일한 신뢰 수준을 지정 되도록 값을 덮어씁니다이 특성에 대해 다른 값을 지정 하는 경우는 <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeDefinition.SupportedDeploymentScopes%2A> 속성입니다.|
|**Type**|필요한 **xs: string** 특성입니다.<br /><br /> SharePoint 프로젝트 항목에 대 한 식별자입니다. 사용자 지정 SharePoint 프로젝트 항목 형식에서 식별자가 전달 하는 문자열을 <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute>입니다. 자세한 내용은 [방법: SharePoint 프로젝트 항목 형식 정의](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)합니다.<br /><br /> Visual Studio를 사용 하 여 포함 된 기본 제공 SharePoint 프로젝트 항목에 대 한 식별자 목록에 대해서 [확장 SharePoint 프로젝트 항목](../sharepoint/extending-sharepoint-project-items.md)합니다.|

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|선택적 요소입니다.<br /><br /> SharePoint 프로젝트 항목에 연관 된 사용자 지정 데이터 항목의 컬렉션을 나타냅니다.<br /><br /> 하나만 포함할 수 있습니다 **ExtensionData** 요소입니다.|
|[FeatureProperties](../sharepoint/featureproperties-element.md)|선택적 요소입니다.<br /><br /> SharePoint에 배포 될 때 기능을 사용 하 여 포함 된 속성 값의 컬렉션을 나타냅니다.<br /><br /> 하나만 포함할 수 있습니다 **FeatureProperties** 요소입니다.|
|[파일](../sharepoint/files-element.md)|선택적 **FileCollectionType** 요소입니다.<br /><br /> 기능 요소 파일 등의 SharePoint 프로젝트 항목 및 종속 비 SharePoint 프로젝트의 출력을 사용 하 여 배포할 파일을 지정 합니다.<br /><br /> 포함 된 **파일** 또는 **ProjectItemFolder** 요소 중 하나만 합니다.|
|[ProjectItemFolder](../sharepoint/projectitemfolder-element.md)|선택적 **ProjectItemFolderType** 요소입니다.<br /><br /> 매핑된 폴더를 나타냅니다.<br /><br /> 포함 된 **파일** 또는 **ProjectItemFolder** 요소 중 하나만 합니다.|
|[SafeControls](../sharepoint/safecontrols-element.md)|선택적 요소입니다.<br /><br /> ASPX 컨트롤 및 SharePoint 사이트의 모든 ASPX 페이지에 액세스 하려면 모든 사용자에 대 한 안전한 것으로 지정 된 웹 파트의 컬렉션을 나타냅니다.<br /><br /> 하나만 포함할 수 있습니다 **SafeControls** 요소입니다.|

### <a name="parent-elements"></a>부모 요소
 없음

## <a name="element-information"></a>요소 정보

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema.xsd|
|**비어 있을 수 있습니다.**|아니요|

## <a name="see-also"></a>참고자료
[SharePoint 프로젝트 항목 스키마 rseference](../sharepoint/sharepoint-project-item-schema-reference.md)
