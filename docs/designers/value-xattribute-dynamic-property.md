---
title: Value(XAttribute 동적 속성)
ms.date: 11/04/2016
ms.topic: reference
apiname:
- XAttribute.Value
apitype: Assembly
ms.assetid: 019733d2-e050-4120-b537-831cd3fc008e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fefa3d13f1a38b5d1c329fa9df9220e13e769b1c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634526"
---
# <a name="value-xattribute-dynamic-property"></a>Value(XAttribute 동적 속성)

XML 특성의 값을 가져오거나 설정합니다.

## <a name="syntax"></a>구문

```xaml
attrib.Value
```

## <a name="property-valuereturn-value"></a>속성 값/반환 값

이 특성의 값이 들어 있는 <xref:System.String>입니다.

## <a name="exceptions"></a>예외

|예외 형식|조건|
| - |---------------|
|<xref:System.ArgumentNullException>|설정 시 `value`가 `null`인 경우|

## <a name="remarks"></a>설명

이 속성은 <xref:System.Xml.Linq.XAttribute.Value%2A> 클래스의 <xref:System.Xml.Linq.XAttribute?displayProperty=fullName> 속성과 동일하지만 이 동적 속성은 변경 알림도 지원합니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>
- [XAttribute 클래스 동적 속성](../designers/value-xattribute-dynamic-property.md)
- [특성](../designers/attribute-xelement-dynamic-property.md)