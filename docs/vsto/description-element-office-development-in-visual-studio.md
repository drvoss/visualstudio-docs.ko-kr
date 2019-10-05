---
title: '&lt;설명&gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.custom: secdec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- description element
- <description> element
- application manifests [Office development in Visual Studio], <description> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ede5ac920c1d40402504544a13f8a00905b82e80
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972384"
---
# <a name="ltdescriptiongt-element-office-development-in-visual-studio"></a>&lt;설명&gt; 요소 (Visual Studio에서 Office 개발)
  `description` 네임스페이스의 `vstov4` 요소는 Microsoft Office 응용 프로그램의 COM 추가 기능 대화 상자에 나타나는 Office 솔루션에 대한 설명을 저장합니다.

## <a name="syntax"></a>구문

```xml
<description>
</description>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 선택 사항입니다. `description` 요소는 `vstov4` 네임스페이스에 있습니다. Microsoft Office 애플리케이션의 COM 추가 기능 대화 상자에 표시되는 추가 기능에 대한 설명이 포함됩니다.

 `description` 요소에는 특성 또는 요소가 없습니다.

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="description"></a>설명
 다음 코드 예제에서는 `description` 를 사용하여 배포된 애플리케이션 수준 솔루션의 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]요소를 보여 줍니다. 이 코드 예제는에서 제공 하는 더 큰 예제의 일부입니다 [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)합니다.

### <a name="code"></a>코드

```xml
<vstov4:description>
  ContosoOutlookAddIn - Outlook add-in
  created with Visual Studio Tools for Office
</vstov4:description>
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션에 대 한 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션의 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 애플리케이션 매니페스트](../deployment/clickonce-application-manifest.md)