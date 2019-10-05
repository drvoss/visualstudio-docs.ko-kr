---
title: Xml(XElement 동적 속성) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
api_name:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 368b18e7524e0cff31139de67f8092f9069246bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68148052"
---
# <a name="xml-xelement-dynamic-property"></a>Xml(XElement 동적 속성)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

요소의 서식이 지정되지 않은 XML 내용을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```  
elem.Xml  
```  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 요소의 서식이 지정되지 않은 XML 내용을 나타내는 <xref:System.String>입니다.  
  
## <a name="remarks"></a>설명  
 이 속성은 <xref:System.Xml.Linq.XNode.ToString%28System.Xml.Linq.SaveOptions%29> 매개 변수가 <xref:System.Xml.Linq.XNode?displayProperty=fullName>으로 설정된 `SaveOptions` 클래스의 <xref:System.Xml.Linq.SaveOptions> 메서드와 동일합니다.  
  
## <a name="see-also"></a>참고 항목  
 [XAttribute 클래스 동적 속성](../designers/xelement-class-dynamic-properties.md)   
 [값](../designers/value-xelement-dynamic-property.md)
