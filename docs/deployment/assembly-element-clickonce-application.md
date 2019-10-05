---
title: '&lt;어셈블리&gt; 요소 (ClickOnce 응용 프로그램) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b629243920021adc3833f43f268f05638029dc7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900762"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;어셈블리&gt; 요소 (ClickOnce 응용 프로그램)
응용 프로그램 매니페스트에 대 한 최상위 요소입니다.

## <a name="syntax"></a>구문

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `assembly` 요소는 루트 요소와가 필요 합니다. 포함 된 첫 번째 요소 여야 합니다는 `assemblyIdentity` 요소입니다. 매니페스트 요소는 다음 네임 스페이스 중 하나 여야 합니다.

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 이러한 네임 스페이스를 상속 하거나 태그를 지정 하 여 어셈블리의 자식 요소 여야 합니다.

 `assembly` 요소에는 다음 특성이 있습니다.

|특성|설명|
|---------------|-----------------|
|`manifestVersion`|필수 요소. 합니다 `manifestVersion` 특성으로 설정 되어 있어야 `1.0`합니다.|

## <a name="example"></a>예제
 다음 코드 예제는 `assembly` 요소에 대 한 응용 프로그램 매니페스트에서 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 응용 프로그램입니다. 이 코드 예제는에서 제공 하는 더 큰 예제의 일부입니다 [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)합니다.

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
```

## <a name="see-also"></a>참고자료
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)
- [\<어셈블리 > 요소](../deployment/assembly-element-clickonce-deployment.md)
