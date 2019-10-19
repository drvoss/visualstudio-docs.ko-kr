---
title: 워크플로 디자이너-보정 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Compensate.UI
ms.assetid: 7347c947-bfff-4bad-becd-5cd23e7b24cd
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65203663214e6bc82a4a7b20af9caa25bfd98ee4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650649"
---
# <a name="compensate-activity-designer"></a>Compensate 활동 디자이너

**보정** 활동 디자이너는 <xref:System.Activities.Statements.Compensate> 활동을 만들고 구성 하는 데 사용 됩니다.

## <a name="the-compensate-activity"></a>Compensate 활동

<xref:System.Activities.Statements.Compensate> 활동은 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>에 포함된 활동에 대해 <xref:System.Activities.Statements.CompensableActivity>를 명시적으로 호출합니다. <xref:System.Activities.Statements.Compensate>, <xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A> 또는 <xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>의 <xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>에서 <xref:System.Activities.Statements.CompensableActivity> 활동을 사용하지 않는 경우 <xref:System.Activities.Statements.Compensate.Target%2A> 속성을 지정해야 합니다.

<xref:System.Activities.Statements.CompensationToken>에 의해 지정된 <xref:System.Activities.Statements.Compensate.Target%2A>은 <xref:System.Activities.Statements.CompensableActivity>의 <xref:System.Activities.Statements.CompensableActivity.Body%2A>가 성공적으로 완료된 후 <xref:System.Activities.Statements.CompensableActivity>를 명시적으로 확인하거나 보정하는 수단을 제공합니다.

### <a name="using-the-compensate-activity-designer"></a>Compensate 활동 디자이너 사용

**보정** 활동 디자이너는 **도구 상자**의 **트랜잭션** 범주에 있습니다. **도구 상자**를 열려면 워크플로 디자이너 왼쪽에 있는 **도구 상자** 탭을 선택 합니다. 또는 **보기** 메뉴에서 **도구 상자** 를 선택 하거나 **ctrl** +**alt** +**X**를 누릅니다.

**보정** 활동 디자이너를 **도구 상자** 에서 끌어 활동을 배치할 위치 (예: <xref:System.Activities.Statements.Sequence>에 있는 워크플로 디자이너 화면에 놓을 수 있습니다. 활동 디자이너를 삭제 하면 기본 <xref:System.Activities.Activity.DisplayName%2A> 보정을 사용 하 여 <xref:System.Activities.Statements.Compensate> 활동이 만들어집니다. **보정** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 <xref:System.Activities.Activity.DisplayName%2A> 값을 편집할 수 있습니다.

### <a name="the-compensate-properties"></a>보정 속성

다음 표에서는 <xref:System.Activities.Statements.CancellationScope> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. @No__t_0 속성은 속성 표 또는 워크플로 디자이너 화면에서 편집할 수 있습니다. 속성 표에서 <xref:System.Activities.Statements.Compensate.Target%2A> 속성을 편집 합니다.

|속성 이름|필요한 공간|사용 현황|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Compensate> 활동의 선택적 이름을 지정합니다. 기본값은 Compensate입니다.|
|<xref:System.Activities.Statements.Compensate.Target%2A>|True|이 <xref:System.Activities.InArgument%601> 활동의 <xref:System.Activities.Statements.CompensationToken>이 들어 있는 <xref:System.Activities.Statements.Compensate>을 지정합니다.|

## <a name="see-also"></a>참조

- [트랜잭션](../workflow-designer/transaction-activity-designers.md)
- [CompensableActivity](../workflow-designer/compensableactivity-activity-designer.md)
- [Compensate 활동 디자이너](../workflow-designer/compensate-activity-designer.md)
- [Confirm](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)