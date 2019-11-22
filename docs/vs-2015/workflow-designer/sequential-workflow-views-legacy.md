---
title: Sequential Workflow Views (Legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflow views
- sequential workflows, views
ms.assetid: 135f24b9-1b37-442b-9ef8-f0f2108a3212
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 859fa44b44a295dc3e9f27fc168092a9fe2beebf
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292364"
---
# <a name="sequential-workflow-views-legacy"></a>순차 워크플로 뷰(레거시)
[!INCLUDE[vs2010](../includes/vs2010-md.md)]에서는 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 또는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 대상으로 하는 데 사용할 수 있는 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 제공합니다.

 [!INCLUDE[wfd2](../includes/wfd2-md.md)]에서는 친숙한 [!INCLUDE[wf](../includes/wf-md.md)] 사용자 인터페이스를 사용하여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 애플리케이션을 시각적으로 만들 수 있습니다. [!INCLUDE[wf](../includes/wf-md.md)] 애플리케이션은 활동이라고 하는 워크플로 프로세스 단계로 구성됩니다. To create a workflow, compose activities on the design surface by dragging their respective activity designers from **Toolbox** onto the design surface.

 When you create a sequential workflow, which is a [SequentialWorkflowActivity](https://go.microsoft.com/fwlink?LinkID=65040), three views of the workflow are available. These views are accessible from the **Workflow** menu and from the context menu on the design surface.

 다음 표에서는 각 뷰의 이름과 설명을 보여 줍니다.

|메뉴/탭 옵션|설명|
|----------------------|-----------------|
|**View SequentialWorkflow**|Right-click the design surface and select the **View SequentialWorkflow** option from the context menu to display the **Sequential Workflow** view, which shows the activity-based graphical representation of the sequential workflow. Or select **View SequentialWorkflow** from the **Workflow** menu.|
|**View Cancel Handler**|Right-click the design surface and select the **View Cancel Handler** option from the context menu to display the **Sequential Workflow** view, which shows the [CancellationHandlerActivity](https://go.microsoft.com/fwlink?LinkID=65050) activity associated with the workflow. Or select **View Cancel Handler** from the **Workflow** menu.|
|**View Fault Handler**|Right-click the design surface and select the **View Fault Handler** option from the context menu to display the **Faults** view, which shows the [FaultHandlersActivity](https://go.microsoft.com/fwlink?LinkID=65055) activity associated with the workflow. Or select **View Fault Handler** from the **Workflow** menu.|

 For more information about similar views, see [Activity Views (Legacy)](../workflow-designer/activity-views-legacy.md).

## <a name="see-also"></a>관련 항목:
 [Activity Views (Legacy)](../workflow-designer/activity-views-legacy.md) [Creating Legacy Workflow Projects](../workflow-designer/creating-legacy-workflow-projects.md) [Workflow Authoring Modes](https://go.microsoft.com/fwlink?LinkID=65014)