---
title: Browse and Select a .NET Type Dialog Box | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d8e25ad181202a2c7994c116e2220426ca3d8509
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297611"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>.NET 유형 선택 대화 상자
In the **Properties** window, dialog boxes, or designers such as the variable designer, when you select **Browse for Types…** from a list of data types, is the **Browse and Select a .NET Type** dialog box (referred to in an abbreviated form as the “type browser”). 이 대화 상자의 어셈블리 및 프로젝트 트리 뷰에서 형식을 선택할 수 있습니다.

 이 대화 상자는 다음을 비롯한 여러 가지 사용자 시나리오에서 사용됩니다.

- 변수 또는 인수의 형식을 설정할 때

- 제네릭 동작의 형식을 선택할 때

- <xref:System.Activities.Statements.TryCatch> 활동에 catch를 추가할 때

> [!NOTE]
> 형식 브라우저는 Visual Basic 가변 배열 형식을 표시할 수 있지만 다차원 배열 형식을 표시할 수 없습니다. See [Jagged Arrays](https://go.microsoft.com/fwlink/?LinkId=195226) and [Multidimensional Arrays](https://go.microsoft.com/fwlink/?LinkId=195227) for details.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>형식 브라우저에서 값 또는 참조 형식 선택

#### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>형식 브라우저에서 값 또는 참조 형식을 선택하려면

1. In the **Type Name** box, enter the name of the type that you want to use.

2. 다음 작업 중 하나를 수행합니다.

    - Once the name of the type that you want to use appears in the tree in the **Type Name** box, double-click the type to select it.

    - Type enough characters in the **Type Name** box to uniquely identify the type that you want to use and then press enter to select the type

#### <a name="to-select-a-generic-type-from-the-type-browser"></a>형식 브라우저에서 제네릭 형식을 선택하려면

1. In the **Type Name** box, type in the name of the type that you want to use.

2. Once the name of the type that you want to use appears in the tree in the **Type Name** box, click the type to select it to cause drop-down boxes appear.

     Select the type that you want to use to close the generic from the drop-down boxes, and then click **OK**.

## <a name="types-displayed-in-the-type-browser"></a>형식 브라우저에 표시된 형식
 형식 브라우저에 표시되는 형식은 형식 브라우저의 시작 방식에 따라 달라질 수 있습니다. If the type browser was launched from a workflow project inside of **vs2010**, by default all of the types in the referenced assemblies and referenced projects are shown. If the type browser was launched from outside of a **vs2010** project system (such as in a rehosted workflow application or in a standalone workflow file), then by default the types from all of the assemblies loaded in the AppDomain are shown.

 활동 디자이너 개발자는 형식 브라우저의 형식을 필터링할 수 있습니다. 특정 활동에서 형식의 하위 집합만 표시되는 경우가 있습니다. 예를 들어 <xref:System.Activities.Statements.TryCatch> 활동의 경우 <xref:System.Exception>에서 파생된 형식만 형식 브라우저에 표시됩니다.

## <a name="filtering-search-results-in-the-type-browser"></a>형식 브라우저에서 검색 결과 필터링
 The list of types in the **Type Name** box gets shorter as you type more characters to find a match. 필터링된 목록에는 정규화된 이름 또는 약식 이름이 입력한 문자열로 시작되는 형식만 표시됩니다.

 예를 들어 다음과 같은 가치를 제공해야 합니다.

1. Typing **Operation** matches <xref:System.OperationCanceledException> but not <xref:System.InvalidOperationException>. <xref:System.InvalidOperationException>을 찾으려면 System.I 또는 Invalid를 입력해야 합니다.

2. Typing **Generic** matches <xref:System.GenericUriParser> but not types in the <xref:System.Collections.Generic> namespace. <xref:System.Collections.Generic> 네임스페이스의 형식을 검색하려면 해당 네임스페이스의 정규화된 이름을 입력해야 합니다.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>형식 브라우저 대화 상자를 사용하여 서비스 계약 선택
 서비스 계약 형식을 선택할 때 형식 브라우저는 <xref:System.ServiceModel.ServiceContractAttribute> 특성이 있는 형식만 보여줍니다.

## <a name="see-also"></a>관련 항목:
 [활동 디자이너 사용](../workflow-designer/using-the-activity-designers.md)