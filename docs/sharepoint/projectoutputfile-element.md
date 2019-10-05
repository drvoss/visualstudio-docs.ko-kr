---
title: ProjectOutputFile 요소 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectOutputFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2673b22bf502f019f0a10361c9d0cef9d5ac1b8c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62816839"
---
# <a name="projectoutputfile-element"></a>ProjectOutputFile 요소
  SharePoint에 배포할 때 프로젝트 항목과 함께 포함할 별도 프로젝트의 출력을 나타냅니다.

## <a name="syntax"></a>구문

```xml
<ProjectOutputFile ProjectId = "GUID of the project"
    ProjectPath = "Relative path of the project"
    Target = "Deployment path of the project output"
    Type = "Type of deployment for the project output" />
```

## <a name="type"></a>형식
 **ProjectOutputFileType**

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|**ProjectId**|필요한 **xs: string** 특성입니다.<br /><br /> 포함 하려는 출력을 포함 하는 종속 프로젝트의 GUID입니다. 이에 해당 합니다 **ProjectGuid** 종속 프로젝트 파일의 요소입니다.|
|**ProjectPath**|필요한 **xs: string** 특성입니다.<br /><br /> 프로젝트 파일 이름에 포함할 출력을 포함 하는 종속 프로젝트를 포함 하 여 상대 경로입니다. SharePoint 프로젝트 항목을 포함 하는 SharePoint 프로젝트의 루트 폴더에 상대적인이 경로가입니다.|
|**Target**|선택적 **xs: string** 특성입니다.<br /><br /> 종속 프로젝트 출력을 SharePoint 서버의 배포 루트 폴더를 기준으로 배포 하는 경로입니다. 지정 된 배포 형식에 의해 결정 됩니다 배포 루트 폴더를 **형식** 특성입니다.<br /><br /> 자세한 내용은 설명을 참조 합니다 **배포 경로** 및 **Deployment Root** 속성을 SharePoint 프로젝트 항목에 [SharePoint 개발 솔루션](../sharepoint/developing-sharepoint-solutions.md)합니다.|
|**Type**|필요한 **xs: string** 특성입니다.<br /><br /> 형식 종속 프로젝트의 출력에 사용할 배포입니다. 가능한 값에 대 한 자세한 정보에 대 한 설명을 참조 합니다 **배포 유형** 에서 SharePoint 프로젝트 항목의 속성 [SharePoint 개발 솔루션](../sharepoint/developing-sharepoint-solutions.md)합니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[파일](../sharepoint/files-element.md)|SharePoint에 배포 될 때 SharePoint 프로젝트 항목을 사용 하 여 포함할 파일을 지정 합니다.|

## <a name="remarks"></a>설명
 사용 된 **ProjectOutputFile** SharePoint 프로젝트 항목의 배포에는 프로젝트의 출력을 포함 하는 요소입니다. 다른 프로젝트 또는 프로젝트 항목을 포함 하는 동일한 프로젝트를 지정할 수 있습니다. 자세한 내용은 [프로젝트 항목에 패키징 및 배포 정보를 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)합니다.

## <a name="element-information"></a>요소 정보

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema.xsd|
|**비어 있을 수 있습니다.**|아니요|

## <a name="see-also"></a>참고자료
- [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)
- [프로젝트 항목에 패키징 및 배포 정보를 제공 합니다.](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
- [SharePoint 솔루션 개발](../sharepoint/developing-sharepoint-solutions.md)
