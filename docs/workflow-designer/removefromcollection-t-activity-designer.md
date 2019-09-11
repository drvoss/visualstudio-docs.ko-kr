---
title: 워크플로 디자이너-RemoveFromCollection&lt;T&gt; 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.RemoveFromCollection`1.UI
ms.assetid: 6617ba26-c8bc-4aed-b746-112bf490d288
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b3a43c05f8be4806cf10098a4df673903494756
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62933742"
---
# <a name="removefromcollectiont-activity-designer"></a>RemoveFromCollection\<T > 활동 디자이너

합니다 **RemoveFromCollection\<T >** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.RemoveFromCollection%601> 활동입니다.

## <a name="the-removefromcollectiontactivity"></a>RemoveFromCollection\<T > 활동

<xref:System.Activities.Statements.RemoveFromCollection%601> 활동은 지정한 항목을 특정 컬렉션에서 제거합니다.

### <a name="using-the-removefromcollectiont-activity-designer"></a>Removefromcollection\<T > 활동 디자이너

액세스는 **RemoveFromCollection\<T >** 활동 디자이너에는 **컬렉션** 범주의 **도구 상자**합니다.
합니다 **RemoveFromCollection\<T >** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 활동 일반적으로 배치 하는 등 어디서 나 워크플로 디자이너 화면에 끌어 놓 및 내부는 <xref:System.Activities.Statements.Sequence>합니다. 이렇게 한 <xref:System.Activities.Statements.RemoveFromCollection%601> 기본값을 사용 하 여 활동 <xref:System.Activities.Activity.DisplayName%2A> RemoveFromCollection의 < Int32\>합니다. <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **RemoveFromCollection < T\> ** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자. 다른 속성은 속성 표에서 편집해야 합니다.

### <a name="the-removefromcollectiont-properties"></a>RemoveFromCollection < T\> 속성

다음 표는 <xref:System.Activities.Statements.RemoveFromCollection%601> 속성 디자이너에서 사용 되는 방법을 설명 합니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.RemoveFromCollection%601> 활동의 선택적 이름입니다. 기본값은 RemoveFromCollection < Int32\>합니다.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Item%2A>|True|제거할 항목의 **컬렉션\<T >** 합니다. 이 항목은 형식의 *T*, 형식인 *TypeArgument*합니다. 이 항목을 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|
|<xref:System.Activities.Statements.RemoveFromCollection%601.Collection%2A>|True|항목을 제거 해야 하는 컬렉션입니다. 이 컬렉션은 형식 **ICollection < TypeArgument\>합니다.** 컬렉션을 지정 하려면 속성 표에 Visual Basic 식을 입력 합니다.|
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601>에 포함된 항목의 형식 T입니다. 기본적으로이 *TypeArgument* 유형이 설정 되어 **Int32**합니다. 유형을 변경 하려면 값을 변경 합니다 *TypeArgument* 속성 표의 콤보 상자에서.|
|<xref:System.Activities.Activity%601.Result%2A>|False|지정된 항목이 컬렉션에서 제거되었는지 여부를 나타내는 값입니다. 결과에 바인딩할 변수를 지정하려면 속성 표에 변수를 입력합니다.|

## <a name="see-also"></a>참고자료

- [컬렉션](../workflow-designer/collection-activity-designers.md)
- [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)
- [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)
- [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)