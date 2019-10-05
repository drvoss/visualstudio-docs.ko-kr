---
title: '&lt;addin&gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <addIn> element
- addin element
- <addin> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3ab7b0617f09b98c9e30c7f198ef0e2aaa301e33
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62931003"
---
# <a name="ltaddingt-element-office-development-in-visual-studio"></a>&lt;addin&gt; 요소 (Visual Studio에서 Office 개발)
  합니다 **추가 기능** 의 요소를 `vstav3` 네임 스페이스는 Microsoft Office VSTO 추가 기능 및 Visual Studio를 사용 하 여 개발 하는 문서 수준 사용자 지정 관련 정보를 포함 합니다.

## <a name="syntax"></a>구문

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customization>
    </customization>
  </application
</addIn>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 **addin** 의 요소를 `vstav3` 네임 스페이스는 Office 솔루션 및 Microsoft Office 응용 프로그램에 대 한 정보를 포함 합니다. 이 요소는 `vstav3=urn:schemas-microsoft-com:vsta.v3`네임스페이스에 있어야 합니다. 자식 요소도 이 네임스페이스에 있어야 합니다.

 `addin` 요소에는 특성이 없습니다.

 `addin` 요소에는 다음 자식 요소가 있습니다.

### <a name="entrypoints"></a>entryPoints
 필수 요소. 합니다 **진입점** 요소에 설명 되어 [ &#60;진입점&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="update"></a>업데이트
 필수 요소. 합니다 **업데이트할** 요소에 설명 되어 [ &#60;업데이트&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/update-element-office-development-in-visual-studio.md).

### <a name="postactions"></a>postActions
 선택 사항입니다. 합니다 **postActions** 요소에 설명 되어 [ &#60;postActions&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/postactions-element-office-development-in-visual-studio.md).

### <a name="application"></a>애플리케이션
 필수 요소. 합니다 **응용 프로그램** 요소에 설명 되어 [ &#60;응용&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/application-element-office-development-in-visual-studio.md).

## <a name="document-level-customization-example"></a>문서 수준 사용자 지정 예제

### <a name="description"></a>설명
 다음 코드 예제는 **addin** 요소를 사용 하 여 배포 되는 문서 수준 Office 솔루션의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]합니다. 이 코드 예제는에서 제공 하는 더 큰 예제의 일부입니다 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.

### <a name="code"></a>코드

```xml
<vstav3:addIn
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">
  <vstav3:entryPointsCollection>
    <vstav3:entryPoints>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.ThisWorkbook">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet1">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet2">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet3">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
  <vstav3:update
    enabled="true">
    <vstav3:expiration
      maximumAge="7"
      unit="days" />
  </vstav3:update>
  <vstav3:application>
    <vstov4:customizations
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
      <vstov4:customization>
        <vstov4:document
          solutionId="73e" />
      </vstov4:customization>
    </vstov4:customizations>
  </vstav3:application>
</vstav3:addIn>
```

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="description"></a>설명
 다음 코드 예제는 **addin** 요소를 사용 하 여 배포 된 응용 프로그램 수준 Office 솔루션에서 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]합니다. 이 코드 예제는에서 제공 하는 더 큰 예제의 일부입니다 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.

### <a name="code"></a>코드

```xml
<vstav3:addIn
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">
  <vstav3:entryPointsCollection>
    <vstav3:entryPoints>
      <vstav3:entryPoint
        class="ContosoOutlookAddIn.ThisAddIn">
        <assemblyIdentity
          name="ContosoOutlookAddIn"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
  <vstav3:update
    enabled="true">
    <vstav3:expiration
      maximumAge="7"
      unit="days" />
  </vstav3:update>
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
</vstav3:addIn>
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션의 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)