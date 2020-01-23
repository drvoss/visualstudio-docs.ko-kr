---
title: 워크플로 디자이너-기능 컬렉션<T> 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb00679001cc09b8fdfa68f898923ac208b32c4e
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76115319"
---
# <a name="addtocollectiont-activity-designer"></a>\<T > 활동 디자이너의 작업 모음 컬렉션

**\<t >** activity designer를 사용 하 여 <xref:System.Activities.Statements.AddToCollection%601> 활동을 만들고 구성 하는 데 사용 됩니다.

## <a name="the-addtocollectiont-activity"></a>\<T > 활동의 작업 모음 컬렉션

<xref:System.Activities.Statements.AddToCollection%601> 활동은 컬렉션에 항목을 추가합니다.

### <a name="using-the-addtocollectiont-activity-designer"></a>\<T > 활동 디자이너를 사용 하 여 작업 컬렉션 사용

워크플로 디자이너의 **도구 상자** 탭을 클릭 하 여 액세스 하는 **도구 상자**의 **컬렉션** 범주에 있는 작업 모음\<> 활동 디자이너의 작업 **모음 컬렉션** 에서 찾을 수 있습니다. 또는 **보기** 메뉴에서 **도구 상자** 를 선택 하거나 **ctrl**+**alt**+**X**를 누릅니다.

**도구 상자** **\<t >** 활동 디자이너를 끌어 <xref:System.Activities.Statements.Sequence>내부와 같이 활동을 배치할 워크플로 디자이너 화면에 놓을 수 있습니다. **\<t >** activity designer를 사용 하 여 작업 컬렉션을 삭제 하면 <xref:System.Activities.Activity.DisplayName%2A> <\>의 기본를 사용 하 여 <xref:System.Activities.Statements.AddToCollection%601> 활동이 만들어집니다. 기본적으로 *Typeargument* 는 **Int32**입니다. TypeArgument는 속성 표에서 변경할 수 있습니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 **< t\>** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 편집할 수 있습니다. 다른 속성은 속성 표에서 편집해야 합니다.

### <a name="the-addtocollectiont-properties"></a>\<T > 속성을 하는 방법 컬렉션

다음 표에서는 <xref:System.Activities.Statements.AddToCollection%601> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.

|속성 이름|필수|용도|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> 활동의 이름입니다. 기본값은 < Int32\>입니다. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|\<T > 컬렉션에 추가할 항목입니다. 이 항목은 유형 *T*이며 *typeargument*유형입니다. 이 항목을 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|항목이 추가될 컬렉션입니다. 이 컬렉션은 **ICollection < TypeArgument 형식\>** 입니다. 컬렉션을 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601>에 포함된 항목의 형식 T입니다. 기본적으로이 형식 *인수* 형식은 **Int32**로 설정 됩니다. 형식을 변경 하려면 속성 표의 콤보 상자에서 *Typeargument* 의 값을 변경 합니다.|

## <a name="see-also"></a>참조

- [수집](../workflow-designer/collection-activity-designers.md)
- [\<T > 활동 디자이너의 작업 모음 컬렉션](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)
- [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)
