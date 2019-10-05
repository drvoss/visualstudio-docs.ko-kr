---
title: '&lt;어셈블리&gt; 요소 (ClickOnce 배포) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b639a7f95cfb59844fa37963730e22ead450482
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62929071"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;어셈블리&gt; 요소 (ClickOnce 배포)
배포 매니페스트에 대 한 최상위 요소입니다.

## <a name="syntax"></a>구문

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `assembly` 요소는 루트 요소와가 필요 합니다. 포함 된 첫 번째 요소 여야 합니다는 `assemblyIdentity` 요소입니다. 매니페스트 요소는 다음 네임 스페이스에 있어야 합니다.: `urn:schemas-microsoft-com:asm.v1`하십시오 `urn:schemas-microsoft-com:asm.v2`, 및 `http://www.w3.org/2000/09/xmldsig#`합니다. 이러한 네임 스페이스를 상속 하거나 태그를 지정 하 여 어셈블리의 자식 요소 여야 합니다.

 `assembly` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`manifestVersion`|필수 요소. 이 특성으로 설정 되어 있어야 `1.0`합니다.|

## <a name="example"></a>예제
 다음 코드 예제는 `assembly` 요소를 사용 하 여 배포 된 응용 프로그램에 대 한 배포 매니페스트의 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]합니다. 이 코드 예제는에 대해 제공 된 큰 예제의 일부 합니다 [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md) 항목입니다.

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
```

## <a name="see-also"></a>참고자료
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)
- [\<어셈블리 > 요소](../deployment/assembly-element-clickonce-application.md)