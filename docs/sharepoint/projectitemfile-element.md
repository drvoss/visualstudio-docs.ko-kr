---
title: ProjectItemFile 요소 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57c491c79030eea1a01024235c01aec425d5994c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562364"
---
# <a name="projectitemfile-element"></a>ProjectItemFile 요소
  기능 요소를 포함할 파일을 프로젝트 항목을 사용 하 여 SharePoint에 배포 될 때와 같은 SharePoint 파일을 나타냅니다.

## <a name="syntax"></a>구문

```xml
<ProjectItemFile Source = "Name of the file"
    Target = "Deployment path of the file"
    Type = "Type of deployment for the file" />
```

## <a name="type"></a>형식
 **ProjectItemFileType**

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|**소스**|필요한 **xs: string** 특성입니다.<br /><br /> 프로젝트 항목을 사용 하 여 배포 파일의 이름입니다.|
|**Target**|선택적 **xs: string** 특성입니다.<br /><br /> 배포 루트 폴더를 기준으로 SharePoint에서 파일이 배포 되는 경로입니다. 지정 된 배포 형식에 의해 결정 됩니다 배포 루트 폴더를 **형식** 특성입니다. 경우는 **대상** 특성을 지정 하지 않으면에서 지정한 이름의 파일이 폴더에 배포 합니다 **원본** 특성입니다.<br /><br /> 자세한 내용은 설명을 참조 합니다 **배포 경로** 및 **Deployment Root** 속성을 SharePoint 프로젝트 항목에 [SharePoint 개발 솔루션](../sharepoint/developing-sharepoint-solutions.md)합니다.|
|**Type**|필요한 **xs: string** 특성입니다.<br /><br /> 파일에 대 한 배포의 형식입니다. 가능한 값에 대 한 자세한 정보에 대 한 설명을 참조 합니다 **배포 유형** 에서 SharePoint 프로젝트 항목의 속성 [SharePoint 개발 솔루션](../sharepoint/developing-sharepoint-solutions.md)합니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[파일](../sharepoint/files-element.md)|SharePoint에 배포 될 때 SharePoint 프로젝트 항목을 사용 하 여 포함할 파일을 지정 합니다.|

## <a name="remarks"></a>설명
 일반적으로 참조 되는 SharePoint 파일 **ProjectItemFile** 요소가 기능 요소 파일 포함 (*Elements.xml*), 목록 정의 대 한 스키마 파일 (*Schema.xml*), 및 웹 파트에 대 한 웹 파트 정의 파일 (*.webpart*).

## <a name="element-information"></a>요소 정보

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema.xsd|
|**비어 있을 수 있습니다.**|아니요|

## <a name="see-also"></a>참고자료
- [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)
