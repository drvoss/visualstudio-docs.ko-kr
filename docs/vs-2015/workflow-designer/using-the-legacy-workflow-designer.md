---
title: Using the Legacy Workflow Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2fa11cd0b29f3b8ee6008b8c0b3369b16812f0e5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302787"
---
# <a name="using-the-legacy-workflow-designer"></a>레거시 Workflow Designer 사용
[!INCLUDE[wfd2](../includes/wfd2-md.md)] 또는 [!INCLUDE[vs2010](../includes/vs2010-md.md)]를 대상으로 하려는 경우 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]에서 제공하는 레거시 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 사용할 수 있습니다.

 It is accessed by selecting either the **.NET Framework 3.0** option or the **.NET Framework 3.5** option in the drop down list at the top of the **New Project** window. The default option in [!INCLUDE[vs2010](../includes/vs2010-md.md)] is **.NET Framework 4** which is used to create [!INCLUDE[wf](../includes/wf-md.md)] applications that target the [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)].

 [!INCLUDE[wfd2](../includes/wfd2-md.md)]에서는 친숙한 [!INCLUDE[wf](../includes/wf-md.md)] 사용자 인터페이스를 사용하여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 애플리케이션을 시각적으로 만들 수 있습니다. [!INCLUDE[wf](../includes/wf-md.md)] 애플리케이션은 활동이라고 하는 워크플로 프로세스 단계로 구성됩니다. To create a workflow, compose activities on the design surface by dragging their respective activity designers from **Toolbox** onto the design surface.

 다음 표에서는 Windows Workflow Foundation용 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 주요 기능을 보여 줍니다.

|기능|설명|
|-------------|-----------------|
|활동 끌어서 놓기|Drag activities from the **Toolbox** onto the design surface to create a workflow.|
|속성 브라우저|The standard **Properties** window in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] is used to configure the properties of an activity.|
|확대/축소|The binoculars **Zoom Level** icon is located below the vertical scroll bar on the right side of the design surface. Click the binoculars and select a zoom percentage to cause the workflow graphic to zoom in or out. You can also use the **Pan** icon magnifying glass cursor options to zoom in and out.|
|이동|The **Pan** icon, a circle that contains four crossed arrows pointing in four directions, is located below the vertical scroll bar on the right side of the design surface just below the binoculars zoom icon. 팬 아이콘을 클릭하면 팝업 메뉴가 나타나 다음과 같은 커서 옵션을 제공합니다.<br /><br /> -   The **Zoom In** magnifying glass cursor lets you zoom in by clicking the design surface.<br />-   The **Zoom Out** magnifying glass cursor lets you zoom out by clicking the design surface.<br />-   The **Navigation Tool** hand cursor lets you "grab" and shift the view of a workflow in the design surface.<br />-   The **Default** arrow cursor lets you switch from the other cursors back to the default arrow cursor.|
|자동 스크롤|워크플로가 큰 경우 디자인 화면의 가시 영역을 바깥으로 활동을 배치할 수 있습니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서는 활동을 배치할 위치와 가장 가까운 디자인 화면의 가장자리 쪽으로 활동을 끌 수 있습니다. 그러면 디자인 화면 뷰가 자동으로 그 방향으로 이동합니다.|
|스마트 태그|완전히 구성되지 않거나 올바르지 않게 구성된 활동은 느낌표 아이콘으로 표시됩니다. 이 아이콘을 클릭하면 해당 활동에 대한 구성 요구 사항 보여 주는 드롭다운 목록이 나타납니다. You can then use the **Properties** window to configure the activity appropriately. 활동의 모든 속성이 올바르게 구성되면 느낌표 아이콘이 사라집니다.|

## <a name="in-this-section"></a>단원 내용
 [Visual Studio 워크플로 창(레거시)](../workflow-designer/visual-studio-workflow-windows-legacy.md)

 [레거시 워크플로 프로젝트 만들기](../workflow-designer/creating-legacy-workflow-projects.md)

 [순차 워크플로 뷰(레거시)](../workflow-designer/sequential-workflow-views-legacy.md)

 [레거시 워크플로 활동](../workflow-designer/legacy-workflow-activities.md)

 [워크플로에서 테마 사용(레거시)](../workflow-designer/using-themes-in-workflows-legacy.md)

 [레거시 상태 시스템 워크플로 디자이너 사용](../workflow-designer/using-the-legacy-state-machine-workflow-designer.md)

 [레거시 활동 디자이너 사용](../workflow-designer/using-the-legacy-activity-designer.md)

 [Windows Workflow Foundation용 레거시 디자이너 UI 도움말](../workflow-designer/legacy-designer-for-windows-workflow-foundation-ui-help.md)

## <a name="see-also"></a>관련 항목:
 [Developing Workflows](https://go.microsoft.com/fwlink?LinkID=65010)