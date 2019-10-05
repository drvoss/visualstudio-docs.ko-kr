---
title: ProjectItemFolder 요소 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 124716f8c40a8adc0a0ae1a28cda21dcb5e00ddf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62562704"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder 요소
  매핑된 폴더를 나타냅니다.

## <a name="syntax"></a>구문

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>형식
 **ProjectItemFolderType**

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|**Target**|필요한 **xs: string** 특성입니다.<br /><br /> 배포 루트 폴더를 기준으로, 해당 하는 매핑된 폴더는 SharePoint 설치 폴더의 경로입니다. 지정 된 배포 형식에 의해 결정 됩니다 배포 루트 폴더를 **형식** 특성입니다.<br /><br /> 자세한 내용은 설명을 참조 합니다 **배포 경로** 및 **Deployment Root** 속성을 SharePoint 프로젝트 항목에 [SharePoint 개발 솔루션](../sharepoint/developing-sharepoint-solutions.md)합니다.|
|**Type**|필요한 **xs: string** 특성입니다.<br /><br /> 매핑된 폴더에 대 한 배포의 형식입니다. 가능한 값에 대 한 자세한 정보에 대 한 설명을 참조 합니다 **배포 유형** 에서 SharePoint 프로젝트 항목의 속성 [SharePoint 개발 솔루션](../sharepoint/developing-sharepoint-solutions.md)합니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint 프로젝트 항목을 나타냅니다. 이 요소는의 필수 루트 요소는 *.spdata* 파일입니다.|

## <a name="remarks"></a>설명
 매핑된 폴더에 대 한 자세한 내용은 참조 하세요. [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)합니다.

## <a name="element-information"></a>요소 정보

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema.xsd|
|**비어 있을 수 있습니다.**|아니요|

## <a name="see-also"></a>참고자료
- [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)
- [방법: 매핑된 폴더 추가 및 제거](../sharepoint/how-to-add-and-remove-mapped-folders.md)
