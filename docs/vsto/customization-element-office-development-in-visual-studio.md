---
title: '&lt;사용자 지정&gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 798cb2e7a8526e97a3d97240e181ef2e35ed21b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956062"
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;사용자 지정&gt; 요소 (Visual Studio에서 Office 개발)
  `customization` 네임스페이스의 `vstov4` 요소는 특정 Office 솔루션에 대해 설명합니다. 문서 수준 사용자 지정 및 VSTO 추가 기능에 대한 자식 요소가 서로 다릅니다.

## <a name="syntax-for-document-level-customizations"></a>문서 수준 사용자 지정에 대 한 구문

```xml
<customization
  id
  <document
    solutionId
  />
</customization>
```

## <a name="syntax-for-vsto-add-ins"></a>VSTO 추가 기능에 대한 구문

```xml
<customization
  id
  <appAddin
    application
    loadBehavior
    keyName>
  <friendlyName></friendlyName>
  <description></description>
  <formRegions></formRegions>
</customization>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `customization` 요소에는 사용자 지정 관련 정보가 포함됩니다. 이 요소는 `vstov4=urn:schemas-microsoft-com:vsto.v4`네임스페이스에 있어야 합니다. 각 Office 솔루션에 대해 하나의 `customization` 요소가 있습니다. 예를 들어 다중 프로젝트 배포에서 세 개의 Office 솔루션을 배포하면 애플리케이션 매니페스트에 세 개의 `customization` 요소가 있습니다.

 어셈블리의 자식 요소도 이 네임스페이스에 있어야 합니다.

 `customization` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`id`|다중 프로젝트 배포의 경우 필수 요소입니다. `id` 요소는 Office 솔루션을 고유하게 식별합니다.|

### <a name="document-level-customizations"></a>문서 수준 사용자 지정
 `customization` 요소에는 다음 자식 요소가 있습니다.

#### <a name="document"></a>문서
 합니다 `document` 요소에는 `vstov4` 네임 스페이스에 정의 된 [ &#60;문서&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/document-element-office-development-in-visual-studio.md).

### <a name="vsto-add-ins"></a>VSTO 추가 기능
 `customization` 요소에는 다음 자식 요소가 있습니다.

#### <a name="appaddin"></a>appAddin
 합니다 `appAddin` 요소에는 `vstov4` 네임 스페이스에 정의 된 [ &#60;appAddin&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).

## <a name="example-of-a-document-level-customization"></a>문서 수준 사용자 지정의 예

### <a name="description"></a>설명
 다음 코드 예제에서는 문서 수준 사용자 지정의 `customization` 요소를 보여 줍니다. 이 코드 예제는에서 제공 하는 더 큰 예제의 일부입니다 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.

### <a name="code"></a>코드

```xml
<vstov4:customization>
  <vstov4:document
    solutionId="73e" />
</vstov4:customization>
```

## <a name="example-of-a-vsto-add-in"></a>VSTO 추가 기능에 대 한 예제

### <a name="description"></a>설명
 다음 코드 예제는 `customization` VSTO 추가 기능에 대 한 요소입니다. 양식 영역을 포함하는 Outlook VSTO 추가 기능입니다. 이 코드 예제는에서 제공 하는 더 큰 예제의 일부입니다 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.

### <a name="code"></a>코드

```xml
<vstov4:customization>
  <vstov4:appAddIn
    application="Outlook"
    loadBehavior="3"
    keyName="ContosoOutlookAddIn">
    <vstov4:friendlyName>
      ContosoOutlookAddIn
    </vstov4:friendlyName>
    <vstov4:description>
      ContosoOutlookAddIn - Outlook VSTO Add-in
      created with Visual Studio Tools for Office
    </vstov4:description>
    <vstov4:formRegions>
      <vstov4:formRegion
          name="OutlookAddIn1.FormRegion1">
        <vstov4:messageClass name="IPM.Note" />
        <vstov4:messageClass name="IPM.Contact" />
        <vstov4:messageClass name="IPM.Appointment" />
      </vstov4:formRegion>
    </vstov4:formRegions>
  </vstov4:appAddIn>
</vstov4:customization>
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션의 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)