---
title: AddToCollection&lt;T&gt; 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.AddToCollection`1.UI
ms.assetid: f7fc0702-164e-4370-8946-bb2f9f9384b7
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4e63486ca7e057fdd1bfe0de73e44dc4951462e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977214"
---
# <a name="addtocollectionlttgt-activity-designer"></a>AddToCollection&lt;T&gt; 활동 디자이너
합니다 **AddToCollection\<T >** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.AddToCollection%601> 활동입니다.  
  
## <a name="the-addtocollectiont-activity"></a>AddToCollection\<T > 활동  
 <xref:System.Activities.Statements.AddToCollection%601> 활동은 컬렉션에 항목을 추가합니다.  
  
### <a name="using-the-addtocollectiont-activity-designer"></a>AddToCollection를 사용 하 여\<T > 활동 디자이너  
 **AddToCollection\<T >** 활동 디자이너에서 찾을 수 있습니다 합니다 **컬렉션** 범주의 합니다 **도구 상자**, 를클릭하여액세스 **도구 상자** 탭의 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **AddToCollection\<T >** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면 아무 곳에 나 작업은 일반적으로, 등 배치를 <xref:System.Activities.Statements.Sequence>. 이렇게 한 <xref:System.Activities.Statements.AddToCollection%601> 기본값을 사용 하 여 활동 <xref:System.Activities.Activity.DisplayName%2A> AddToCollection의\<Int32 >. (기본적으로 *TypeArgument* 됩니다 **Int32**합니다. 속성 표에서 이를 변경할 수 있습니다. <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **AddToCollection\<T >** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자. 다른 속성은 속성 표에서 편집해야 합니다.  
  
### <a name="the-addtocollectiont-properties"></a>AddToCollection\<T > 속성  
 다음 표에서는 <xref:System.Activities.Statements.AddToCollection%601> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.AddToCollection%601> 활동의 이름입니다. 기본값은 AddToCollection\<Int32 >. <xref:System.Activities.Activity.DisplayName%2A> 값은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.AddToCollection%601.Item%2A>|True|컬렉션에 추가할 항목\<T >입니다. 이 항목은 형식의 *T*, 형식인 *TypeArgument*합니다. 이 항목을 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|  
|<xref:System.Activities.Statements.AddToCollection%601.Collection%2A>|True|항목이 추가될 컬렉션입니다. 이 컬렉션은 형식 **ICollection\<TypeArgument >** 합니다. 컬렉션을 지정하려면 속성 표에 Visual Basic 식을 입력합니다.|  
|*TypeArgument*|True|<xref:System.Collections.Generic.ICollection%601>에 포함된 항목의 형식 T입니다. 기본적으로이 *TypeArgument* 유형이 설정 되어 **Int32**합니다. 유형을 변경 하려면 값을 변경 합니다 *TypeArgument* 속성 표의 콤보 상자에서.|  
  
## <a name="see-also"></a>참고 항목  
 [컬렉션](../workflow-designer/collection-activity-designers.md)   
 [AddToCollection\<T > 활동 디자이너](../workflow-designer/addtocollection-t-activity-designer.md)   
 [ClearCollection\<T>](../workflow-designer/clearcollection-t-activity-designer.md)   
 [ExistsInCollection\<T>](../workflow-designer/existsincollection-t-activity-designer.md)   
 [RemoveFromCollection\<T>](../workflow-designer/removefromcollection-t-activity-designer.md)