---
title: Using the Legacy Activity Designer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, configuring
- custom activities
- Activity Designer
- child activities, adding
- activities, adding child
- activities, creating custom
ms.assetid: 2fea8a05-6e58-423d-94bf-a822b15ffb80
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a13aeeb3394ee6b8896376c0e7d520b90fb56fa6
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74302818"
---
# <a name="using-the-legacy-activity-designer"></a>레거시 활동 디자이너 사용
이 항목에서는 레거시 [!INCLUDE[wfd1](../includes/wfd1-md.md)]에서 활동 디자이너를 사용하는 방법에 대해 설명합니다. 레거시 디자이너는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 하는 경우에 사용합니다.

 활동 디자이너를 사용하면 사용자 지정 활동을 직접 만들 수 있습니다.

## <a name="creating-a-custom-activity"></a>사용자 지정 활동 만들기
 활동 디자이너를 사용하여 사용자 지정 활동을 만들려면 다음 단계를 따르세요.

1. On the **Project** menu, click **Add Activity**.

2. Select the **Activity** or **Activity (with code separation)** template.

   1. Use the **Activity** template to create an activity with the activity definition and the user code in same code file.

   2. Use the **Activity (with code separation)** template to create an activity with the activity definition expressed as workflow markup and the user code in a separate code file.

3. Type an activity name or keep the default name, and then click **Add**.

   You can also create a set of custom activities by creating a new project of type **Workflow Activity Library**. For more information about this project type, see [How to: Create a Workflow Activity Library (Legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md).

## <a name="configuring-an-activity"></a>활동 구성
 활동 디자이너가 활성 상태일 때 속성 브라우저를 사용하여 다음 표에 나열된 속성을 구성할 수 있습니다.

|속성|주석|
|--------------|--------------|
|**이름**|활동 이름입니다.|
|**Base Class**|활동이 파생되는 기본 클래스입니다. The default base class is [SequenceActivity](https://go.microsoft.com/fwlink?LinkID=65020). In the **Properties** window, click the **Base Class** ellipses **[…]** to select another base class in the [Browse and Select a .NET Type Dialog Box (Legacy)](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box-legacy.md).|
|**설명**|활동의 사용자 정의 설명입니다.|
|**Enabled**|Set to **True** by default to enable activity execution and validation. Set to **False** to disable activity execution and validation. For information about activity execution and validation, see [Developing Workflow Activities](https://go.microsoft.com/fwlink?LinkID=65024).|

## <a name="adding-child-activities"></a>자식 활동 추가
 도구 상자에서 디자인 중인 활동으로 자식 활동을 끌어 놓을 수 있습니다. 그런 다음 속성 브라우저를 사용하여 각 자식 활동을 구성할 수 있습니다.

## <a name="see-also"></a>관련 항목:
 [Developing Workflow Activities](https://go.microsoft.com/fwlink?LinkID=65024) [Creating Custom Activities](https://go.microsoft.com/fwlink?LinkID=65021) [Legacy Workflow Activities](../workflow-designer/legacy-workflow-activities.md) [Custom Activities Samples](https://go.microsoft.com/fwlink?LinkID=65022) [How to: Create a Workflow Activity Library (Legacy)](../workflow-designer/how-to-create-a-workflow-activity-library-legacy.md) [Using the Legacy Workflow Designer](../workflow-designer/using-the-legacy-workflow-designer.md)