---
title: 워크플로 디자이너-Persist 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c97d916d00d1c976b4e27381f55e42cbb7cb0db
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004128"
---
# <a name="persist-activity-designer"></a>Persist 활동 디자이너

**Persist** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.Persist> 활동입니다.

## <a name="the-persist-activity"></a>Persist 활동

<xref:System.Activities.Statements.Persist> 활동은 워크플로를 디스크에 저장합니다(가능한 경우). <xref:System.Activities.Statements.Persist> 활동과 같은 비지속성 영역에서는 <xref:System.Activities.Statements.TransactionScope> 활동을 실행할 수 없습니다. 비지속성 범위 내에서 <xref:System.Activities.Statements.Persist> 활동을 사용할 경우 런타임에 예외가 throw됩니다.

### <a name="using-the-persist-activity-designer"></a>Persist 활동 디자이너 사용

**Persist** 활동 디자이너에서 찾을 수 있습니다는 **런타임** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구 상자** 탭 (또는 선택할 **도구 상자** 에서 합니다 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)

**지속** 활동 디자이너에서 끌 수 있습니다를 **도구 상자** 작업은 일반적으로, 등 배치 위치는 워크플로 디자이너 화면에 끌어 놓 및는 <xref:System.Activities.Statements.Sequence>합니다. 이렇게를 <xref:System.Activities.Statements.Persist> 기본값을 사용 하 여 활동 **DisplayName** Persist입니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **Persist** 활동 디자이너 또는 **DisplayName** 속성 그리드의 상자.

### <a name="the-persist-properties"></a>Persist 속성

다음 표에서는 <xref:System.Activities.Statements.Persist> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있습니다 하 고 그 중 일부는 워크플로 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Persist> 활동의 이름입니다. 기본값은 Persist입니다. 표시 이름이 꼭 필요하지 않더라도 표시 이름을 사용하는 것이 좋습니다.|

## <a name="see-also"></a>참고자료

- [런타임](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)