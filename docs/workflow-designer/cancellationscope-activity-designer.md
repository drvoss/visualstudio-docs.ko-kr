---
title: 워크플로 디자이너-CancellationScope 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43a818be208c7e07ef74a8f35923f3042bb8fad5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009792"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope 활동 디자이너

합니다 **CancellationScope** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.CancellationScope> 활동입니다.

## <a name="the-cancellationscope-activity"></a>CancellationScope 활동

<xref:System.Activities.Statements.CancellationScope> 활동을 사용하여 실행할 활동과 해당 활동에 대한 취소 논리를 지정할 수 있습니다.

### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope 활동 디자이너 사용

합니다 **CancellationScope** 활동 디자이너에서 찾을 수 있습니다 합니다 **트랜잭션** 범주의 **도구 상자**합니다. 열려는 **도구 상자**를 선택 합니다 **도구 상자** 워크플로 디자이너의 탭 합니다. 또는 선택할 **도구 상자** 에서 합니다 **뷰** 메뉴 또는 키를 눌러 **Ctrl**+**Alt** + **X**합니다.

합니다 **CancellationScope** 활동 디자이너에서 끌 수 있습니다 **도구 상자** 활동을 배치 하는 등으로 내 어디서 나 워크플로 디자이너 화면에 끌어 놓 및는 <xref:System.Activities.Statements.Sequence>합니다. 삭제 된 **CancellationScope** 활동 디자이너를 만듭니다를 <xref:System.Activities.Statements.CancellationScope> 기본값을 사용 하 여 작업 <xref:System.Activities.Activity.DisplayName%2A> CancellationScope입니다. 편집 합니다 <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 **CancellationScope** 활동 디자이너입니다. 편집할 수도 있습니다는 **DisplayName** 속성 그리드의 상자입니다.

### <a name="the-cancellationscope-properties"></a>CancellationScope 속성

다음 표에서는 <xref:System.Activities.Statements.CancellationScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. <xref:System.Activities.Activity.DisplayName%2A> 속성 속성 표에서 편집할 수 있지만 다른 속성을 워크플로 디자이너 화면에서 편집 해야 합니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 활동의 선택적 이름입니다. 기본값은 CancellationScope입니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|취소 논리가 제공되는 활동을 지정합니다. 추가할 합니다 <xref:System.Activities.Statements.CancellationScope.Body%2A> 활동에서 활동 **도구 상자** 에 **본문** 상자에 **CancellationScope** 활동 디자이너입니다. 여기에 작업 놓기 "힌트 텍스트를 추가 합니다.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|취소가 없을 경우 실행 되는 작업을 지정 합니다. 추가할 합니다 <xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A> 활동에서 활동 **도구 상자** 에 **CancellationHandler** 상자에 **CancellationScope** 활동 디자이너입니다. 여기에 작업 놓기 "힌트 텍스트를 추가 합니다.|

## <a name="see-also"></a>참고자료

- [트랜잭션](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)