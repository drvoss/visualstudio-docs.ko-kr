---
title: 워크플로 디자이너 CancellationScope 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.CancellationScope.UI
ms.assetid: 2c85d663-b219-4142-9866-7693ffd46379
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a2fd36d81f774ca48cca170b8a4a256d73cf1f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650708"
---
# <a name="cancellationscope-activity-designer"></a>CancellationScope 활동 디자이너

**CancellationScope** 활동 디자이너는 <xref:System.Activities.Statements.CancellationScope> 활동을 만들고 구성 하는 데 사용 됩니다.

## <a name="the-cancellationscope-activity"></a>CancellationScope 활동

<xref:System.Activities.Statements.CancellationScope> 활동을 사용하여 실행할 활동과 해당 활동에 대한 취소 논리를 지정할 수 있습니다.

### <a name="using-the-cancellationscope-activity-designer"></a>CancellationScope 활동 디자이너 사용

**CancellationScope** 활동 디자이너는 **도구 상자**의 **트랜잭션** 범주에 있습니다. **도구 상자**를 열려면 워크플로 디자이너의 **도구 상자** 탭을 선택 합니다. 또는 **보기** 메뉴에서 **도구 상자** 를 선택 하거나 **ctrl** +**alt** +**X**를 누릅니다.

**CancellationScope** 활동 디자이너를 **도구 상자** 에서 끌어 활동을 배치할 위치 (예: <xref:System.Activities.Statements.Sequence>에 있는 워크플로 디자이너 화면에 놓을 수 있습니다. **CancellationScope** 활동 디자이너를 삭제 하면 CancellationScope의 기본 <xref:System.Activities.Activity.DisplayName%2A>를 사용 하 여 <xref:System.Activities.Statements.CancellationScope> 활동이 만들어집니다. **CancellationScope** activity 디자이너의 헤더에서 <xref:System.Activities.Activity.DisplayName%2A> 값을 편집 합니다. 또한 속성 표의 **DisplayName** 상자에서 편집할 수 있습니다.

### <a name="the-cancellationscope-properties"></a>CancellationScope 속성

다음 표에서는 <xref:System.Activities.Statements.CancellationScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. @No__t_0 속성은 속성 표에서 편집할 수 있지만 다른 속성은 워크플로 디자이너 화면에서 편집 해야 합니다.

|속성 이름|필요한 공간|사용 현황|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CancellationScope> 활동의 선택적 이름입니다. 기본값은 CancellationScope입니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.CancellationScope.Body%2A>|True|취소 논리가 제공되는 활동을 지정합니다. @No__t_0 활동을 추가 하려면 **도구 상자** 의 활동을 **CancellationScope** 활동 디자이너의 **본문** 상자로 끌어 놓습니다. "여기에 작업 놓기" 힌트 텍스트를 추가 합니다.|
|<xref:System.Activities.Statements.CancellationScope.CancellationHandler%2A>|True|취소가 있는 경우 실행 되는 작업을 지정 합니다. @No__t_0 활동을 추가 하려면 **도구 상자** 의 활동을 **CancellationScope** 활동 디자이너의 **CancellationHandler** 상자로 끌어 놓습니다. "여기에 작업 놓기" 힌트 텍스트를 추가 합니다.|

## <a name="see-also"></a>참조

- [트랜잭션](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)