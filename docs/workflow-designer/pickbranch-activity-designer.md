---
title: PickBranch 활동 디자이너-워크플로 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.PickBranch.UI
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6c452cb4fd5b8a343473204c2b2bee614383ebb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63003628"
---
# <a name="pickbranch-activity-designer"></a>PickBranch 활동 디자이너

<xref:System.Activities.Statements.PickBranch>는 들어오는 이벤트에 의해 트리거되는 <xref:System.Activities.Statements.Pick> 활동 내에서 이벤트 기반의 실행 경로를 제공합니다.

## <a name="pickbranch"></a>PickBranch

<xref:System.Activities.Statements.PickBranch> 개체는 <xref:System.Activities.Statements.Pick.Branches%2A> 활동의 <xref:System.Activities.Statements.Pick> 컬렉션에 포함되어 있습니다. 각 <xref:System.Activities.Statements.PickBranch>는 <xref:System.Activities.Statements.Pick> 활동의 분기에 포함되며 트리거 역할을 하는 일부 들어오는 이벤트에 따라 실행될 수 있습니다. 이러한 방식으로 워크플로 디자이너는 이벤트 기반 제어 흐름 모델링을 제공합니다. 각 <xref:System.Activities.Statements.PickBranch>에는 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 및 <xref:System.Activities.Statements.PickBranch.Action%2A>이 포함되어 있습니다.

### <a name="how-to-use-the-pick-activity-designer"></a>Pick 활동 디자이너를 사용하는 방법

액세스는 **PickBranch** 디자이너를 **제어 흐름** 범주에는 **도구 상자**합니다.

두 개의 빈 <xref:System.Activities.Statements.PickBranch> 사용 하 여 개체의 이름을 표시 **Branch1** 및 **분기 2** 요소로 기본적으로 생성 되는 <xref:System.Activities.Statements.Pick> 활동 때 합니다 **선택** 활동 디자이너는 워크플로 디자이너에 처음에 삭제 됩니다. 이러한 각 <xref:System.Activities.Statements.PickBranch.DisplayName%2A> 속성 값을 편집할 수 있습니다 합니다 **PickBranch** 디자이너 머리글 또는 합니다 **속성** 각 분기에 대 한 창.

추가 하는 방법은 두 가지가 <xref:System.Activities.Statements.PickBranch> 개체의 컬렉션에는 <xref:System.Activities.Statements.Pick> 개체: 끌어서 놓기는 **PickBranch** 에서 디자이너를 **도구 상자**, 또는에서 오른쪽 클릭 메뉴를 사용 하 여 내 합니다 **선택** 디자인 화면:

- **PickBranch** 디자이너를 만듭니다를 <xref:System.Activities.Statements.PickBranch> 에서 끌어 올 때 합니다 **도구 상자** 분기 중 하나를 삭제 하 고는 **선택** 에서 activity designer는 워크플로 디자이너 화면입니다. 새 <xref:System.Activities.Statements.PickBranch> 개체는 <xref:System.Activities.Statements.Pick> 디자이너 내에서 컬렉션에 이미 포함되어 있는 기존 <xref:System.Activities.Statements.PickBranch> 요소의 왼쪽 또는 오른쪽에 배치됩니다. 끌어 올 때를 **PickBranch** 디자이너를 **선택** 마우스를 사용 하 여 디자이너를 **선택** 디자이너 세로 파란색-회색 밴드를 사용 하 여 위치를 나타내기 위해는 <xref:System.Activities.Statements.PickBranch> 특정된 마우스 위치에 대 한 추가 됩니다.

- 마우스 오른쪽 단추로 클릭 **선택** 활동 디자이너 (에서 **PickBranch** 디자이너)를 상황에 맞는 메뉴를 받은 선택 **분기 만들기** 새 <xref:System.Activities.Statements.PickBranch>합니다. 새 <xref:System.Activities.Statements.PickBranch> 기존의 오른쪽에 추가 됩니다 <xref:System.Activities.Statements.PickBranch> 개체를 **선택** 디자이너입니다.

합니다 **PickBranch** 디자이너를 표시 하기 위해 확장할 수 있습니다 합니다 **트리거** 및 **작업** 상자 또는 해당 헤더의 오른쪽에 있는 이중 캐럿을 클릭 하 여 축소 합니다. 편집 합니다 <xref:System.Activities.Statements.PickBranch.Trigger%2A> 및 <xref:System.Activities.Statements.PickBranch.Action%2A> 각 <xref:System.Activities.Statements.PickBranch> 활동을 끌어서 합니다 **트리거** 및 **작업** 해당 디자이너의 상자.

<xref:System.Activities.Statements.PickBranch> 개체를 <xref:System.Activities.Statements.Pick.Branches%2A> 의 컬렉션을 <xref:System.Activities.Statements.Pick> 개체를 끌어서 놓아 내의 새 위치에서 다시 정렬할 수 있습니다 합니다 **선택** 디자이너. 합니다 **선택** 디자이너 세로 파란색-회색 밴드를 사용 하 여 위치를 나타내기 위해는 <xref:System.Activities.Statements.PickBranch> 는 특정된 마우스 위치에 대 한 추가 됩니다.

<xref:System.Activities.Statements.PickBranch>를 삭제하는 방법은 두 가지입니다.

- 선택 된 **PickBranch** 디자이너를 삭제 합니다.
- 선택 된 **PickBranch** 디자이너를 마우스 오른쪽 단추 클릭 상황에 맞는 메뉴를 가져오고 선택 **삭제**합니다.

선택 해야 합니다 **PickBranch** 디자이너 내에서 작업 중 하나를 선택 하 여 해당 **트리거** 또는 **동작** 이러한 작업 중 하나는 상자 실수로 삭제 아니라 <xref:System.Activities.Statements.PickBranch> 개체입니다.

### <a name="pickbranch-properties-in-the-workflow-designer"></a>Workflow Designer의 PickBranch 속성

다음 표에서 가장 유용한 <xref:System.Activities.Statements.PickBranch> 속성 워크플로 디자이너에서 사용 하는 방법을 설명 합니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|헤더에 표시 되는 친숙 한 이름 합니다 **PickBranch** 디자이너입니다. 기본값은 분기입니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|각 <xref:System.Activities.Statements.PickBranch>에는 <xref:System.Activities.Statements.PickBranch.Trigger%2A>을 호출할 수 있는 <xref:System.Activities.Statements.PickBranch.Action%2A> 활동이 포함되어 있습니다.|
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|각 <xref:System.Activities.Statements.PickBranch>에는 트리거될 경우 실행되는 <xref:System.Activities.Statements.PickBranch.Action%2A>이 포함되어 있습니다.|

## <a name="see-also"></a>참고자료

- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)
- [선택 활동](/dotnet/framework/windows-workflow-foundation/pick-activity)
- [Pick 작업 사용](/dotnet/framework/windows-workflow-foundation/samples/using-the-pick-activity)