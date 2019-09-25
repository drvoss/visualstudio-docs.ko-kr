---
title: 'CA2212: 서비스 구성 요소를 WebMethod를 사용하여 표시하지 마십시오.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b2ace5f6e51fc7a8d29faab14cc2332fd808f93
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231661"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: 서비스 구성 요소를 WebMethod를 사용하여 표시하지 마십시오.

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|범주|Microsoft.Usage|
|주요 변경 내용|주요 변경|

## <a name="cause"></a>원인

에서 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> 상속 되는 형식의 메서드는로 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>표시 됩니다.

## <a name="rule-description"></a>규칙 설명

<xref:System.Web.Services.WebMethodAttribute>ASP.NET를 사용 하 여 만든 XML web services 내의 메서드에 적용 됩니다. 원격 웹 클라이언트에서 호출할 수 있는 메서드를 만듭니다. 메서드와 클래스는 public 이어야 하며 ASP.NET 웹 응용 프로그램에서 실행 되어야 합니다. <xref:System.EnterpriseServices.ServicedComponent>형식은 COM + 응용 프로그램에서 호스팅되며 COM + 서비스를 사용할 수 있습니다. <xref:System.Web.Services.WebMethodAttribute>는 동일한 시나리오에 <xref:System.EnterpriseServices.ServicedComponent> 적합 하지 않기 때문에 형식에 적용 되지 않습니다. 특히 특성 <xref:System.EnterpriseServices.ServicedComponent> 을 메서드에 추가 해도 원격 웹 클라이언트에서 메서드를 호출할 수 없습니다. 및 <xref:System.Web.Services.WebMethodAttribute> 메서드에는 <xref:System.EnterpriseServices.ServicedComponent> 컨텍스트 및 트랜잭션 흐름에 대해 충돌 하는 동작 및 요구 사항이 있으므로 메서드의 동작은 일부 시나리오에서 올바르지 않습니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법

이 규칙 위반 문제를 해결 하려면 <xref:System.EnterpriseServices.ServicedComponent> 메서드에서 특성을 제거 합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시 하지 않는 경우

이 규칙에서는 경고를 표시해야 합니다. 이러한 요소를 결합 하는 것이 올바른 시나리오는 없습니다.

## <a name="see-also"></a>참고 항목

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>