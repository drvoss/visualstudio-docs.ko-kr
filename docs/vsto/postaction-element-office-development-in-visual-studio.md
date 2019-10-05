---
title: '&lt;postAction&gt; 요소 (Visual Studio에서 Office 개발)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53cf47ef9a78ebb54c377e19b4f7fbad444bbfcd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976526"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt; 요소 (Visual Studio에서 Office 개발)
  `postAction` 네임스페이스의 `vstav3` 요소에는 `entrypoint` 요소 및 배포 후 작업과 관련된 모든 `postActionData` 요소가 포함되며 Office 솔루션 설치 후 실행됩니다.

## <a name="syntax"></a>구문

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 `postAction` 요소는 선택적이며 `vstav3` 네임스페이스에 있습니다. 하나의 애플리케이션 매니페스트에서는 각 배포 후 작업에 대해 하나의 `postAction` 요소만 정의할 수 있습니다.

 `postAction` 요소에는 특성이 없습니다.

 `postAction` 에는 다음 요소가 있습니다.

### <a name="entrypoint"></a>entrypoint
 선택 사항입니다. 역할을 합니다 `entryPoint` 요소에는 `vstav3` 네임 스페이스에 정의 된 [ &#60;진입점&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
 선택 사항입니다. 역할을 합니다 `postActionData` 요소에는 `vstav3` 네임 스페이스에 정의 된 [ &#60;postActionData&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>배포 후 작업 예제

### <a name="description"></a>설명
 다음 코드 예제에서는 `postAction` 을 사용하여 배포된 Office 솔루션에 대한 애플리케이션 매니페스트의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]요소를 보여 줍니다. 이 코드 예제는에서 제공 하는 더 큰 예제의 일부입니다 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.

### <a name="code"></a>코드

```xml
<vstav3:postAction>
  <vstav3:entryPoint
    class="PostDeploymentAction.PostDeploymentActionSample">
    <assemblyIdentity
      name="PostDeploymentAction"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="msil" />
  </vstav3:entryPoint>
  <vstav3:postActionData>
  </vstav3:postActionData>
</vstav3:postAction>
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션의 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)
