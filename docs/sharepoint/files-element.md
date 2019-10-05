---
title: 요소 파일 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Files element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3c669b7cc314bc2d7a999e77d5cfb95251789dd8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967372"
---
# <a name="files-element"></a>Files 요소
  기능 요소 파일 등의 SharePoint 프로젝트 항목 및 종속 비 SharePoint 프로젝트의 출력을 사용 하 여 배포할 파일을 지정 합니다.

## <a name="syntax"></a>구문

```xml
<Files>
  <ProjectItemFile.../>
  <ProjectOutputFile.../>
</Files>
```

## <a name="type"></a>형식
 **FileCollectionType**

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성
 없음

### <a name="child-elements"></a>자식 요소

|요소|설명|
|-------------|-----------------|
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|선택적 **ProjectItemFileType** 요소입니다.<br /><br /> 기능 요소를 포함할 파일을 프로젝트 항목을 사용 하 여 SharePoint에 배포 될 때와 같은 SharePoint 파일을 나타냅니다.|
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|선택적 **ProjectOutputFileType** 요소입니다.<br /><br /> SharePoint에 배포할 때 프로젝트 항목과 함께 포함할 프로젝트의 출력을 나타냅니다.|

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint 프로젝트 항목을 나타냅니다. 이 요소는 필수 루트 요소에는 `.spdata` 파일.|

## <a name="element-information"></a>요소 정보

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**스키마 이름**|SharePoint 프로젝트 항목 스키마|
|**유효성 검사 파일**|ProjectItemModelSchema.xsd|
|**비어 있을 수 있습니다.**|아니요|

## <a name="see-also"></a>참고자료
- [SharePoint 프로젝트 항목 스키마 참조](../sharepoint/sharepoint-project-item-schema-reference.md)
