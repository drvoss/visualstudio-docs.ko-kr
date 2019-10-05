---
title: 'CA2212: WebMethod 사용 하 여 서비스 구성 요소를 표시 하지 않음 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6f2e89705e36407e39103296e3eee70482e3d03f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68142477"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212: 서비스 구성 요소를 WebMethod를 사용하여 표시하지 마십시오.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|범주|Microsoft.Usage|
|변경 수준|주요 변경|

## <a name="cause"></a>원인
 상속 되는 형식의 메서드 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> 으로 표시 된 <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>합니다.

## <a name="rule-description"></a>규칙 설명
 <xref:System.Web.Services.WebMethodAttribute> ASP.NET;를 사용 하 여 만든 XML 웹 서비스 메서드에 적용 됩니다. 이 메서드를 호출할 수 있게 원격 웹 클라이언트에서. 공용 및 ASP.NET 웹 응용 프로그램에서 실행 중인 메서드 및 클래스 여야 합니다. <xref:System.EnterpriseServices.ServicedComponent> COM + 응용 프로그램에서 호스팅되는 형식과 COM + 서비스를 사용할 수 있습니다. <xref:System.Web.Services.WebMethodAttribute> 에 적용 되지 않습니다 <xref:System.EnterpriseServices.ServicedComponent> 같은 시나리오에 적합 하지 있기 때문입니다. 특히, 특성을 추가 합니다 <xref:System.EnterpriseServices.ServicedComponent> 메서드 해도 메서드를 호출할 원격 웹 클라이언트에서. 때문에 <xref:System.Web.Services.WebMethodAttribute> 및 <xref:System.EnterpriseServices.ServicedComponent> 메서드가 충돌 하는 동작 및 상황에 맞는 트랜잭션 흐름에 메서드의 동작에 대 한 요구 사항 일부 시나리오에서 잘못 됩니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 이 규칙 위반 문제를 해결 하려면에서 특성 제거는 <xref:System.EnterpriseServices.ServicedComponent> 메서드.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시해야 합니다. 이러한 요소를 결합 하는 올바른 시나리오가 있습니다.

## <a name="see-also"></a>참고 항목
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
