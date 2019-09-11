---
title: 워크플로 디자이너-스위치<T> 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7eb83567a7d59dc02779839a5305b9c1c0329912
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434048"
---
# <a name="switcht-activity-designer"></a>스위치\<T > 활동 디자이너

<xref:System.Activities.Statements.Switch%601> 활동은 지정된 식을 계산하고 연관된 키가 계산에서 얻은 값과 일치하는 활동 컬렉션의 활동을 실행합니다.

**스위치 < T\>**  활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.Switch%601> 워크플로 디자이너에서 작업 합니다.

## <a name="the-switchtactivity"></a>스위치\<T > 활동

<xref:System.Activities.Statements.Switch%601> 활동에는 <xref:System.Activities.Statements.Switch%601.Expression%2A> 및 <xref:System.Activities.Statements.Switch%601.Cases%2A> 사전이 포함되어 있습니다. 각각의 경우 사전에 포함 된 쌍으로 구성 된 *키* 및 역할을 해당 하는 활동 *값*합니다. <xref:System.Activities.Statements.Switch%601> 활동은 <xref:System.Activities.Statements.Switch%601.Expression%2A>을 계산한 후 각 키와 비교하고, 일치하는 항목이 있으면 해당 작업이 실행됩니다. 사전 키는 사전의 같음 비교자로 정의된 같음 형식에 따라 고유해야 하므로 일치하는 항목은 하나만 존재할 수 있습니다. 일치하는 항목이 없으면 <xref:System.Activities.Statements.Switch%601.Default%2A> 활동이 실행됩니다.

## <a name="how-to-use-the-switcht-activity-designer"></a>스위치를 사용 하는 방법을\<T > 활동 디자이너

액세스는 **스위치\<T >** 활동 디자이너에는 **제어 흐름** 범주의 **도구 상자**합니다. Workflow Designer에 놓은 후 표시 합니다 **유형 선택** 제네릭 형식을 지정 하는 사용자에 게 대화 *T* 에 사용 되는 <xref:System.Activities.Statements.Switch%601> 활동입니다. 기본값은 **Int32**합니다. 제네릭 형식 *T* 을 선택한 후에 **스위치 < T\>**  디자이너가 워크플로 디자이너에 추가 됩니다.

속성은 **스위치 < T\>**  디자이너입니다. 이러한 모든 속성을 속성 표에서 편집할 수 있습니다. 일부 속성은 디자이너 화면에서도 편집할 수 있습니다.

다음 표에서는 가장 유용한 <xref:System.Activities.Statements.Switch%601> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Switch%601> 활동 디자이너의 이름을 지정합니다. 기본값은 스위치 < Int32\>합니다. 값을 편집할 수 있습니다 합니다 **속성** 창 하거나 디자이너 머리글에서 직접.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|True|실행할 case를 결정하기 위해 case 컬렉션의 키와 비교하는 데 사용할 식을 지정합니다.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||일치하는 항목이 없는 경우에 실행할 활동을 지정합니다. 클릭 합니다 **작업 추가** 열려는 디자이너에서 단추를 **기본** 상자 활동을 삭제할 수 있습니다.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||계산할 case를 지정합니다. Case를 추가 하려면 클릭 합니다 **새 사례 추가** 아래쪽의 단추 **스위치\<T >** 디자이너입니다. 단추 텍스트 변경 (스위치를 추가 하는 경우 제네릭 형식을 선택한 경우 콤보 상자\<T > String 또는 Enum). 키를 추가한 후는 **Case 값** 상자에서 case 영역이 확장 되 고 작업을 삭제할 수 있습니다 위치 경우의 실행 논리를 정의할 여기에 작업 놓기"힌트 텍스트가 있습니다.|

case 키가 중복되지 않는 한 여러 case를 추가할 수 있습니다. 키가 중복되는 경우 지정한 case 키가 이미 있으며 다른 키를 선택해야 한다는 메시지가 표시된 오류 대화 상자가 나타납니다. 에 **스위치\<T >** 디자이너에 한 case 영역만 번 확장 된 보기에 있을 수 있습니다. case 영역이 축소된 보기로 되어 있는 경우 case 영역을 클릭하면 보기가 확장됩니다. 축소된 case는 디자이너에서 case 내 활동의 표시 이름(있는 경우)이 case 오른쪽에 표시됩니다. 그렇지 않으면 표시 된 **작업 추가** 단추를 클릭 하면 대/소문자를 확장 하 고 작업을 추가할 수 있습니다.

기존 case의 키를 클릭하면 키 레이블이 텍스트 상자로 바뀌어 case 키를 편집할 수 있게 됩니다.

case를 삭제하는 방법은 두 가지입니다.

- case를 선택하여 삭제합니다.

- 선택 된 경우 마우스 오른쪽 단추 클릭 상황에 맞는 메뉴를 표시 및 선택할 **삭제**합니다.

삭제하려면 case 자체를 선택해야 합니다. case 내의 활동을 선택하여 삭제하는 경우 case가 아닌 활동만 삭제됩니다.

## <a name="see-also"></a>참고자료

- [제어 흐름](../workflow-designer/control-flow-activity-designers.md)