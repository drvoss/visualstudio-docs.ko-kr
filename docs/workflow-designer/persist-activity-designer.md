---
title: 워크플로 디자이너-Persist 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 882a68e006ac139d717320b0b8b7ce4d75aceb38
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650114"
---
# <a name="persist-activity-designer"></a>Persist 활동 디자이너

**Persist** 활동 디자이너는 <xref:System.Activities.Statements.Persist> 활동을 만들고 구성 하는 데 사용 됩니다.

## <a name="the-persist-activity"></a>Persist 활동

<xref:System.Activities.Statements.Persist> 활동은 워크플로를 디스크에 저장합니다(가능한 경우). <xref:System.Activities.Statements.Persist> 활동과 같은 비지속성 영역에서는 <xref:System.Activities.Statements.TransactionScope> 활동을 실행할 수 없습니다. 지 속성이 아닌 범위에서 <xref:System.Activities.Statements.Persist> 활동을 사용 하는 경우 런타임에 예외가 throw 됩니다.

### <a name="using-the-persist-activity-designer"></a>Persist 활동 디자이너 사용

**Persist** 활동 디자이너 **는 도구 상자**의 **런타임** 범주에 있습니다 .이 범주에 액세스 하려면 **도구 상자** 탭을 클릭 하거나, **보기** 메뉴에서 **도구 상자** 를 선택 하거나, CTRL + ALT + X를 선택 합니다.

**지속** 활동 디자이너를 **도구 상자** 에서 끌어와 같이 일반적으로 활동을 <xref:System.Activities.Statements.Sequence> 배치 하는 아무 곳에 나 워크플로 디자이너 화면에 놓을 수 있습니다. 그러면 기본 **DisplayName** 이 Persist 인 <xref:System.Activities.Statements.Persist> 활동이 만들어집니다. 이 <xref:System.Activities.Activity.DisplayName%2A>는 **Persist** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 편집할 수 있습니다.

### <a name="the-persist-properties"></a>Persist 속성

다음 표에서는 <xref:System.Activities.Statements.Persist> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 워크플로 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필요한 공간|사용 현황|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Persist> 활동의 이름입니다. 기본값은 Persist입니다. 표시 이름이 꼭 필요하지 않더라도 표시 이름을 사용하는 것이 좋습니다.|

## <a name="see-also"></a>참조

- [런타임](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)