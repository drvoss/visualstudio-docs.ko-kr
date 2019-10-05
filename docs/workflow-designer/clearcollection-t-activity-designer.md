---
title: 워크플로 디자이너-ClearCollection<T> 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ClearCollection`1.UI
ms.assetid: db0e5da2-7b5a-4f1a-864c-f3aeeeeb51a7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cab7ea023524da7e28e2baa2d4e5018cd091c60d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949996"
---
# <a name="clearcollectiont-activity-designer"></a>ClearCollection\<T > 활동 디자이너

합니다 **ClearCollection\<T >** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.ClearCollection%601> 활동입니다.

## <a name="the-clearcollectiont-activity"></a>ClearCollection\<T > 활동

<xref:System.Activities.Statements.ClearCollection%601> 활동은 모든 항목의 지정한 컬렉션을 지웁니다.

### <a name="using-the-clearcollectiont-activity-designer"></a>ClearCollection를 사용 하 여\<T > 활동 디자이너

**ClearCollection\<T >** 활동 디자이너에서 찾을 수 있습니다 합니다 **컬렉션** 범주의 합니다 **도구 상자**, 를클릭하여액세스 **도구 상자** 워크플로 디자이너의 탭 합니다. 또는 선택할 **도구 상자** 에서 합니다 **뷰** 메뉴 또는 키를 눌러 **Ctrl**+**Alt** + **X**합니다.

합니다 **ClearCollection\<T >** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 활동을 배치 하는 등 를내부로어디서나워크플로디자이너화면에끌어놓및<xref:System.Activities.Statements.Sequence>. Activity designer 만들어집니다를 <xref:System.Activities.Statements.ClearCollection%601> 기본값을 사용 하 여 활동 <xref:System.Activities.Activity.DisplayName%2A> ClearCollection의 < Int32\>합니다. (기본적으로 *TypeArgument* 됩니다 **Int32**합니다. TypeArgument 변경할 수 있습니다 속성 표에.) <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **ClearCollection < T\>**  활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자. 다른 속성은 속성 표에서 편집해야 합니다.

### <a name="the-clearcollectiont-properties"></a>ClearCollection\<T > 속성

다음 표에서는 <xref:System.Activities.Statements.ClearCollection%601> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ClearCollection%601> 활동의 선택적 이름을 지정합니다. 기본값은 ClearCollection < Int32\>합니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.ClearCollection%601.Collection%2A>|True|선언할 항목 컬렉션을 지정합니다. 이 컬렉션은 형식 **ICollection\<TypeArgument >.** 컬렉션을 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601>에 포함된 T 형식의 항목을 지정합니다. 기본적으로이 *TypeArgument* 유형이 설정 되어 **Int32**합니다. 유형을 변경 하려면 값을 변경 합니다 *TypeArgument* 속성 표의 콤보 상자에서.|

## <a name="see-also"></a>참고자료

- [컬렉션](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)