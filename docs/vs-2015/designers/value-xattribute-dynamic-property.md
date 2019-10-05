---
title: Value(XAttribute 동적 속성) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XAttribute.Value
api_type:
- Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2b83e4a208553b0ad732cfe927aec02b47e389dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187505"
---
# <a name="value-xattribute-dynamic-property"></a>Value(XAttribute 동적 속성)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML 특성의 값을 가져오거나 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
attrib.Value   
```  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 이 특성의 값이 들어 있는 <xref:System.String>입니다.  
  
## <a name="exceptions"></a>예외  
  
|예외 형식|조건|  
|--------------------|---------------|  
|<xref:System.ArgumentNullException>|설정 시 `value`가 `null`인 경우|  
  
## <a name="remarks"></a>설명  
 이 속성은 <xref:System.Xml.Linq.XAttribute.Value%2A> 클래스의 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> 속성과 동일하지만 이 동적 속성은 변경 알림도 지원합니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>   
 [XAttribute 클래스 동적 속성](../designers/xattribute-class-dynamic-properties.md)   
 [특성](../designers/attribute-xelement-dynamic-property.md)
