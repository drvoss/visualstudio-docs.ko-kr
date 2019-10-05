---
title: '&lt;어셈블리&gt; 요소 (ClickOnce 응용 프로그램) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d619b8b3cd81e5b00fc689077a95ade08f4d7eed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68183476"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;어셈블리&gt; 요소 (ClickOnce 응용 프로그램)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

응용 프로그램 매니페스트에 대 한 최상위 요소입니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
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
 다음 코드 예제는 `assembly` 요소에 대 한 응용 프로그램 매니페스트에서 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] 응용 프로그램입니다. 이 코드 예제는에서 제공 하는 더 큰 예제의 일부입니다 [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)합니다.  
  
```  
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
  
## <a name="see-also"></a>관련 항목  
 [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)   
 [\<assembly> 요소](../deployment/assembly-element-clickonce-deployment.md)
