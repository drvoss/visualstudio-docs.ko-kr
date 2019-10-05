---
title: '&lt;응용 프로그램&gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <application> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 80652f6752b87cf0413b0b3166b0cf3292231c25
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62942914"
---
# <a name="ltapplicationgt-element-office-development-in-visual-studio"></a>&lt;응용 프로그램&gt; 요소 (Visual Studio에서 Office 개발)
  `application` 네임스페이스의 `vstav3` 요소는 Office 솔루션에 대한 설명을 래핑합니다. 문서 수준 사용자 지정 및 VSTO 추가 기능에 대한 자식 요소가 서로 다릅니다.

## <a name="syntax-for-document-level-customizations"></a>문서 수준 사용자 지정에 대 한 구문

```xml
<application>
  <customization
    id
    <document
      solutionId
    />
  </customization>
</application>
```

## <a name="syntax-for-application-level-add-ins"></a>응용 프로그램 수준 추가 기능에 대 한 구문

```xml
<application>
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
</application>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `application` 네임스페이스의 `vstav3` 요소는 `vstov4` 네임스페이스에 포함된 모든 사용자 지정 관련 정보를 래핑하는 노드입니다.

 `application` 요소에는 특성이 없습니다.

 `application` 요소에는 다음 요소가 있습니다.

### <a name="customization"></a>사용자 지정
 역할을 합니다 `customization` 요소에는 `vstov3` 네임 스페이스에 정의 된 [ &#60;사용자 지정&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/customization-element-office-development-in-visual-studio.md).

## <a name="document-level-customization-example"></a>문서 수준 사용자 지정 예제

### <a name="description"></a>설명
 다음 코드 예제에서는 `application` 을 사용하여 배포된 문서 수준 Office 솔루션의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]요소를 보여 줍니다. 이 코드 예제는 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)에서 제공하는 보다 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
    <vstov4:customization>
      <vstov4:document
        solutionId="73e" />
    </vstov4:customization>
  </vstov4:customizations>
</vstav3:application>
```

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="description"></a>설명
 다음 코드 예제에서는 `application` 을 사용하여 배포된 애플리케이션 수준 Office 솔루션의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]요소를 보여 줍니다. 이 코드 예제는 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)에서 제공하는 보다 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstav3:application>
  <vstov4:customizations
    xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
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
  </vstov4:customizations>
</vstav3:application>
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션의 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)