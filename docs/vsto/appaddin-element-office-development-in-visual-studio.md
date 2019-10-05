---
title: '&lt;appAddin&gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <appAddin> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2116576acb06e6291749d9c0176fcf4ebb426739
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953246"
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;appAddin&gt; 요소 (Visual Studio에서 Office 개발)
  합니다 **appAddin** 의 요소를 `vstov4` 네임 스페이스는 VSTO 추가 기능에 대 한 사용자 지정 관련 정보를 저장 합니다.

## <a name="syntax"></a>구문

```xml
<appAddin
  application
  loadBehavior
  keyName>
  <friendlyName>
  <description>
  <formRegions></formRegions>
</appAddin>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 합니다 **appAddin** 요소는 필수 요소 이며는 `vstov4` 네임 스페이스입니다. 하나만 **appAddin** 응용 프로그램 매니페스트에서 정의 된 요소입니다.

 합니다 **appAddin** 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|**application**|필수 요소. Microsoft Office 애플리케이션을 식별합니다. 값은 다음 중 하나일 수 있습니다. Excel, InfoPath, Outlook, PowerPoint, Project, Visio 또는 Word|
|**loadBehavior**|선택 사항입니다. 기본적으로 **loadBehavior** 이 값을 설정 하 여 사용 하도록 설정 됩니다. 디버깅을 위해서는 이 값을 2로 설정하여 VSTO 추가 기능을 사용하지 않도록 설정할 수 있습니다. 자세한 내용은에서 LoadBehavior 값 표를 참조 [VSTO 추가 기능에 대 한 레지스트리 항목](../vsto/registry-entries-for-vsto-add-ins.md)합니다.|
|**keyName**|필수 요소. 이 값은 애플리케이션에서 VSTO 추가 기능을 로드할 때 사용할 레지스트리 키 이름입니다. 자세한 내용은 [VSTO 추가 기능에 대 한 레지스트리 항목](../vsto/registry-entries-for-vsto-add-ins.md)합니다.|

 합니다 **appAddin** 요소에는 다음 자식 요소가 있습니다.

### <a name="friendlyname"></a>friendlyName
 선택 사항입니다. 합니다 **friendlyName** 요소가 설명 되어 [ &#60;friendlyName&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/friendlyname-element-office-development-in-visual-studio.md).

### <a name="description"></a>설명
 선택 사항입니다. 합니다 **설명을** 요소가 설명 되어 [ &#60;설명&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/description-element-office-development-in-visual-studio.md).

### <a name="formregions"></a>formRegions
 양식 영역을 포함하는 Outlook VSTO 추가 기능에 대해서만 필수 요소. 합니다 **formRegions** 요소가 설명 되어 [ &#60;formRegions&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/formregions-element-office-development-in-visual-studio.md).

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="description"></a>설명
 다음 코드 예제를 보여 줍니다 **appAddin** 요소를 사용 하 여 배포 된 Outlook 솔루션의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]합니다. 이 코드 예제는에서 제공 하는 더 큰 예제의 일부입니다 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.

### <a name="code"></a>코드

```xml
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
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션의 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)