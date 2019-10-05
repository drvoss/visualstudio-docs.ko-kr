---
title: '&lt;customHostSpecified&gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 26597796c99d3ab8740812819cf3aa5568e2985b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956181"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;customHostSpecified&gt; 요소 (Visual Studio에서 Office 개발)
  `customHostSpecified` 요소는이 솔루션을 독립 실행형 응용 프로그램 아님을 나타냅니다. Office 솔루션은 Microsoft Office 응용 프로그램 내에서 호스트 되는 구성 요소를 포함 합니다.

## <a name="syntax"></a>구문

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `customHostSpecified` 요소는 Office 솔루션에 필요 합니다. 이 요소는 여 `co.v1` 네임 스페이스 및이 배포 사용자 지정 호스트를 내부에 배포 하는 구성 요소에 포함 되도록 지정 하 고 독립 실행형 응용 프로그램이 아닙니다.

 이 요소는 첫 번째 자식 `<entrypoint>` 응용 프로그램 매니페스트에 요소입니다. 다른 자식 요소가 있을 수 있습니다 `<entrypoint>` 요소 또는 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 설치 하는 동안 유효성 검사 오류를 발생 시킵니다.

 이 요소에는 특성과 자식 요소가 없습니다.

## <a name="example"></a>예제
 다음 코드 예제는 `customHostSpecified` Office 솔루션에 대 한 응용 프로그램 매니페스트에 요소입니다. 이 코드 예제는에서 제공 하는 더 큰 예제의 일부입니다 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션의 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)