---
title: '&lt;formRegions&gt; 요소 (Visual Studio에서 Office 개발)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b978ef47db6b8803b7730aef14173c3eb19b16e8
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674008"
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;formRegions&gt; 요소 (Visual Studio에서 Office 개발)
  합니다 `formRegions` 의 요소를 `vstov4` 네임 스페이스는에서 VSTO 추가 기능을 사용 하 여 연결 된 Microsoft Office Outlook 양식 영역을 포함 합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## <a name="elements-and-attributes"></a>요소 및 특성  
 `formRegions` 네임스페이스의 `vstov4` 요소에는 Outlook VSTO 추가 기능에 대한 모든 `formRegion` 요소가 포함됩니다. 양식 영역을 포함하는 Outlook VSTO 추가 기능에만 필요합니다.  
  
 하나의 응용 프로그램 매니페스트에서는 하나의 `formRegions` 요소만 정의할 수 있습니다.  
  
 `formRegions` 요소에는 특성이 없습니다.  
  
 `formRegions` 요소에는 다음 요소가 있습니다.  
  
### <a name="formregion"></a>formRegion  
 양식 영역을 포함하는 Outlook VSTO 추가 기능에 필요합니다. 합니다 `formRegion` 요소에 정의 된 [ &#60;formRegion&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제  
  
### <a name="description"></a>설명  
 다음 코드 예제에서는 `formRegions` 을 사용하여 배포된 응용 프로그램 수준의 Office 솔루션에 대한 응용 프로그램 매니페스트의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]요소를 보여 줍니다. 이 코드 예제는에서 제공 하는 더 큰 예제의 일부입니다 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.  
  
### <a name="code"></a>코드  
  
```xml  
<vstov4:formRegions>  
  <vstov4:formRegion  
      name="OutlookAddIn1.FormRegion1">  
    <vstov4:messageClass name="IPM.Note" />  
    <vstov4:messageClass name="IPM.Contact" />  
    <vstov4:messageClass name="IPM.Appointment" />  
  </vstov4:formRegion>  
</vstov4:formRegions>  
```  
  
## <a name="see-also"></a>참고자료  
 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)   
 [Office 솔루션의 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce 응용 프로그램 매니페스트](/visualstudio/deployment/clickonce-application-manifest)  
  
  