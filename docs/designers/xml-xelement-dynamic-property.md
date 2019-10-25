---
title: Xml(XElement 동적 속성)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c93aaf3b43a930fe88020738460ec131972a205a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72633519"
---
# <a name="xml-xelement-dynamic-property"></a>Xml(XElement 동적 속성)

요소의 서식이 지정되지 않은 XML 내용을 가져옵니다.

## <a name="syntax"></a>구문

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>속성 값/반환 값

요소의 서식이 지정되지 않은 XML 내용을 나타내는 <xref:System.String>입니다.

## <a name="remarks"></a>설명

이 속성은 <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> 매개 변수가 <xref:System.Xml.Linq.XNode?displayProperty=fullName>으로 설정된 `SaveOptions` 클래스의 <xref:System.Xml.Linq.SaveOptions> 메서드와 동일합니다.

## <a name="see-also"></a>참고 항목

- [XElement 클래스 동적 속성](../designers/attribute-xelement-dynamic-property.md)
- [값](../designers/value-xelement-dynamic-property.md)