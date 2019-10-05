---
title: 특성(XElement 동적 속성)
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 8440fc7d-b3b4-4726-8ec8-492e6af79642
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ec27fe2d7824ca32cbf97dbabac8b7ea6c4aed6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926925"
---
# <a name="attribute-xelement-dynamic-property"></a>특성(XElement 동적 속성)

지정한 확장된 이름에 해당하는 특성 인스턴스를 검색하는 데 사용되는 인덱서를 가져옵니다.

## <a name="syntax"></a>구문

```xaml
elem.Attribute[{namespaceName}attribName]
```

## <a name="property-valuereturn-value"></a>속성 값/반환 값

`XAttribute Item(String expandedName)` 형식의 인덱서입니다. 이 인덱서는 지정된 특성의 확장된 이름을 사용하여 해당하는 <xref:System.Xml.Linq.XAttribute>를 반환하거나 지정된 이름을 가진 특성이 없는 경우 `null`을 반환합니다.

## <a name="remarks"></a>주의

이 속성은 <xref:System.Xml.Linq.XElement.Attribute%2A> 클래스의 <xref:System.Xml.Linq.XElement?displayProperty=fullName> 메서드와 동일합니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=fullName>
- [XAttribute 클래스 동적 속성](../designers/xelement-class-dynamic-properties.md)
- [값](../designers/value-xattribute-dynamic-property.md)