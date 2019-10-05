---
title: Xml(XElement 동적 속성)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XElement.Xml
ms.assetid: 69ab2a33-4fe7-4cfa-97f8-eaf063decb18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7d58dea02a45ccc84e7829da2acdb479eb17dda3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62843955"
---
# <a name="xml-xelement-dynamic-property"></a>Xml(XElement 동적 속성)

요소의 서식이 지정되지 않은 XML 내용을 가져옵니다.

## <a name="syntax"></a>구문

```xaml
elem.Xml
```

## <a name="property-valuereturn-value"></a>속성 값/반환 값

요소의 서식이 지정되지 않은 XML 내용을 나타내는 <xref:System.String>입니다.

## <a name="remarks"></a>주의

이 속성은 <xref:System.Xml.Linq.XNode.ToString(System.Xml.Linq.SaveOptions)> 매개 변수가 <xref:System.Xml.Linq.XNode?displayProperty=fullName>으로 설정된 `SaveOptions` 클래스의 <xref:System.Xml.Linq.SaveOptions> 메서드와 동일합니다.

## <a name="see-also"></a>참고 항목

- [XElement 클래스 동적 속성](../designers/xelement-class-dynamic-properties.md)
- [값](../designers/value-xelement-dynamic-property.md)