---
title: 워크플로 디자이너-Compensate 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c55ecd8e3402d927b11cc00d18d6d134a5b25681
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949840"
---
# <a name="compensate-activity-designer"></a>Compensate 활동 디자이너

합니다 **Compensate** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.Compensate> 활동입니다.

## <a name="the-compensate-activity"></a>Compensate 활동

<xref:System.Activities.Statements.Compensate> 활동은 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>에 포함된 활동에 대해 <xref:System.Activities.Statements.CompensableActivity>를 명시적으로 호출합니다. <xref:System.Activities.Statements.Compensate>, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 또는 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>의 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>에서 <xref:System.Activities.Statements.CompensableActivity> 활동을 사용하지 않는 경우 <xref:System.Activities.Statements.Compensate.Target%2A> 속성을 지정해야 합니다.

<xref:System.Activities.Statements.CompensationToken>에 의해 지정된 <xref:System.Activities.Statements.Compensate.Target%2A>은 <xref:System.Activities.Statements.CompensableActivity>의 <xref:System.Activities.Statements.CompensableActivity.Body%2A>가 성공적으로 완료된 후 <xref:System.Activities.Statements.CompensableActivity>를 명시적으로 확인하거나 보정하는 수단을 제공합니다.

### <a name="using-the-compensate-activity-designer"></a>Compensate 활동 디자이너 사용

**Compensate** 활동 디자이너에서 찾을 수 있습니다 합니다 **트랜잭션** 범주의 합니다 **도구 상자**. 열려는 **도구 상자**를 선택 합니다 **도구 상자** 워크플로 디자이너의 왼쪽에 탭 합니다. 또는 선택할 **도구 상자** 에서 합니다 **뷰** 메뉴 또는 키를 눌러 **Ctrl**+**Alt** + **X**합니다.

**Compensate** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 활동을 배치 하는 등으로 내 어디서 나 워크플로 디자이너 화면에 끌어 놓 및를 <xref:System.Activities.Statements.Sequence>합니다. Activity designer 만들어집니다를 <xref:System.Activities.Statements.Compensate> 기본값을 사용 하 여 작업 <xref:System.Activities.Activity.DisplayName%2A> Compensate입니다. <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **Compensate** 활동 디자이너 또는 **DisplayName** 속성 그리드의 상자입니다.

### <a name="the-compensate-properties"></a>보정 속성

다음 표에서는 <xref:System.Activities.Statements.CancellationScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. <xref:System.Activities.Activity.DisplayName%2A> 워크플로 디자이너 화면 또는 속성 표의 속성을 편집할 수 있습니다. 편집 된 <xref:System.Activities.Statements.Compensate.Target%2A> 속성 표에 속성입니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Compensate> 활동의 선택적 이름을 지정합니다. 기본값은 Compensate입니다.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|이 <xref:System.Activities.InArgument%601> 활동의 <xref:System.Activities.Statements.CompensationToken>이 들어 있는 <xref:System.Activities.Statements.Compensate>을 지정합니다.|

## <a name="see-also"></a>참고자료

- [트랜잭션](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate 활동 디자이너](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)