---
title: SafeControl 요소 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e6b47254a80c9cdadab6ca18f2fb8c3e8540fbd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62827346"
---
# <a name="safecontrol-element"></a>SafeControl 요소
  ASPX 컨트롤 또는 SharePoint 사이트의 모든 ASPX 페이지에 액세스 하려면 모든 사용자에 대 한 보안 지정 된 웹 파트를 나타냅니다.

## <a name="syntax"></a>구문

```xml
<SafeControl Assembly = "Name of assembly that contains the safe control"
    IsSafe = "true/false"
    IsSafeAgainstScript = "true/false"
    Name = "Name of this safe control entry"
    Namespace = "Namespace of the safe control"
    TypeName = "Type of the safe control" />
```

## <a name="attributes-and-elements"></a>특성 및 요소
 다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

|특성|설명|
|---------------|-----------------|
|**어셈블리**|선택적 **xs: string** 특성입니다.<br /><br /> ASPX 컨트롤이 나 웹 파트 정의 되어 있는 어셈블리의 이름입니다. 이 특성이 기본적으로 사용 합니다 **$SharePoint.Project.AssemblyFullName$** 어셈블리 이름에 대 한 대체 가능 매개 변수입니다. 자세한 내용은 [대체 가능 매개 변수](../sharepoint/replaceable-parameters.md)합니다.|
|**IsSafe**|선택적 **xs: boolean** 특성입니다.<br /><br /> ASPX 컨트롤이 나 웹 파트 안전한 신뢰할 수 없는 사용자가 액세스할 수 있는지 여부를 지정 합니다.|
|**IsSafeAgainstScript**|선택적 **xs: boolean** 특성입니다.<br /><br /> 신뢰할 수 없는 사용자가 볼 수 있습니다 또는 ASPX 컨트롤이 나 웹 파트의 속성을 편집 여부를 지정 합니다.|
|**이름**|선택적 **xs: string** 특성입니다.<br /><br /> 컬렉션에서이 안전 컨트롤 항목의 이름입니다.|
|**Namespace**|선택적 **xs: string** 특성입니다.<br /><br /> ASPX 컨트롤이 나 웹 파트의 네임 스페이스입니다.|
|**TypeName**|선택적 **xs: string** 특성입니다.<br /><br /> ASPX 컨트롤이 나 웹 파트의 형식 이름입니다.|

### <a name="child-elements"></a>자식 요소
 없음

### <a name="parent-elements"></a>부모 요소

|요소|설명|
|-------------|-----------------|
|[SafeControls](../sharepoint/safecontrols-element.md)|ASPX 컨트롤 및 SharePoint 사이트의 모든 ASPX 페이지에 액세스 하려면 모든 사용자에 대 한 안전한 것으로 지정 된 웹 파트의 컬렉션을 나타냅니다.|

## <a name="remarks"></a>설명
 안전 컨트롤에 대 한 자세한 내용은 참조 하세요. [프로젝트 항목에 패키징 및 배포 정보를 제공](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)합니다.

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
