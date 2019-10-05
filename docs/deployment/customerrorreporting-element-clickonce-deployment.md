---
title: '&lt;customErrorReporting&gt; 요소 (ClickOnce 배포) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <customErrorReporting> element [ClickOnce deployment manifest]
ms.assetid: 7d31816e-c692-46b5-9cc9-753284b3bcda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d42bd1f7304d9f50b6334d9ac8ddd4f626605d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900373"
---
# <a name="ltcustomerrorreportinggt-element-clickonce-deployment"></a>&lt;customErrorReporting&gt; 요소 (ClickOnce 배포)
오류가 발생할 때 표시할 URI를 지정합니다.

## <a name="syntax"></a>구문

```xml
<customErrorReporting
   uri
/>
```

## <a name="remarks"></a>설명
 이 요소는 선택적입니다. 없으면 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 예외 스택을 보여 주는 오류 대화 상자를 표시 합니다. 경우는 `customErrorReporting` 요소가 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] 를 대신 하 여 지정 된 URI를 표시 합니다 `uri` 매개 변수입니다. 대상 URI 매개 변수로 외부 예외 클래스, 내부 예외 클래스 및 내부 예외 메시지가 포함 됩니다.

 이 요소를 사용 하 여 응용 프로그램에 오류 보고 기능을 추가 합니다. 생성된 된 URI 오류 유형에 대 한 정보를 포함 하므로 웹 사이트에는 정보 및 표시 되는 적절 한 문제 해결 화면 예를 들어, 구문 분석할 수 있습니다.

## <a name="example"></a>예제
 다음 코드 조각과 `customErrorReporting` 요소를 함께 생성된 된 URI 생성할 수 있습니다.

```xml
<customErrorReporting uri=http://www.contoso.com/applications/error.asp />

Example Generated Error:
http://www.contoso.com/applications/error.asp? outer=System.Deployment.Application.InvalidDeploymentException&&inner=System.Deployment.Application.InvalidDeploymentException&&msg=The%20application%20manifest%20is%20signed,%20but%20the%20deployment%20manifest%20is%20unsigned.%20Both%20manifests%20must%20be%20either%20signed%20or%20unsigned.
```

## <a name="see-also"></a>참고자료
- [ClickOnce 배포 매니페스트](../deployment/clickonce-deployment-manifest.md)