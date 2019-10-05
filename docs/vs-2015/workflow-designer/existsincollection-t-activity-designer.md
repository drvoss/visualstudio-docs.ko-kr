---
title: ExistsInCollection&lt;T&gt; 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.ExistsInCollection`1.UI
ms.assetid: 0acf9a13-caf5-4bb4-ba22-ec37d2b7267a
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 263bbf16c72bab5a42dc0ba1465d4c7062333071
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952829"
---
# <a name="existsincollectionlttgt-activity-designer"></a>ExistsInCollection&lt;T&gt; 활동 디자이너
합니다 **ExistsInCollection\<T >** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.ExistsInCollection%601> 활동입니다.  
  
## <a name="the-existsincollectiont-activity"></a>ExistsInCollection\<T > 활동  
 <xref:System.Activities.Statements.ExistsInCollection%601> 활동은 지정된 항목이 특정 컬렉션에 있는지 여부를 결정합니다.  
  
### <a name="using-the-existsincollectiont-activity-designer"></a>ExistsInCollection를 사용 하 여\<T > 활동 디자이너  
 **ExistsInCollection\<T >** 활동 디자이너에서 찾을 수 있습니다 합니다 **컬렉션** 범주의 합니다 **도구 상자**, 를클릭하여액세스 **도구 상자** 탭의 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **뷰** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **ExistsInCollection\<T >** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면의 아무 곳에 나 활동 일반적으로 배치 하는 등 내부는 <xref:System.Activities.Statements.Sequence>합니다. 이렇게 한 <xref:System.Activities.Statements.ExistsInCollection%601> 기본값을 사용 하 여 활동 <xref:System.Activities.Activity.DisplayName%2A> ExistsInCollection의\<Int32 >. (기본적으로 *TypeArgument* 됩니다 **Int32**합니다. 속성 표에서 이를 변경할 수 있습니다.  <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **ExistsInCollection\<T >** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자. 다른 속성은 속성 표에서 편집해야 합니다.  
  
### <a name="the-existsincollectiont-properties"></a>ExistsInCollection\<T > 속성  
 다음 표에서는 <xref:System.Activities.Statements.ExistsInCollection%601> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.ExistsInCollection%601> 활동의 이름입니다. 기본값은 ExistsInCollection\<Int32 >. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Item%2A>|True|컬렉션에 추가할 항목\<T >입니다. 이 항목은 형식의 *T* 유형의 *TypeArgument*합니다. 이 항목을 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|  
|<xref:System.Activities.Statements.ExistsInCollection%601.Collection%2A>|True|항목이 추가될 컬렉션입니다. 이 컬렉션은 형식 **ICollection\<TypeArgument >.** 컬렉션을 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|  
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601>에 포함된 항목의 형식 T입니다. 기본적으로이 *TypeArgument* 유형이 설정 되어 **Int32**합니다. 유형을 변경 하려면 값을 변경 합니다 *TypeArgument* 속성 표의 콤보 상자에서.|  
|<xref:System.Activities.Activity%601.Result%2A>|False|지정된 항목이 컬렉션에 있는지 여부를 나타내는 값입니다. 결과에 바인딩할 변수를 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [컬렉션](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T>](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)