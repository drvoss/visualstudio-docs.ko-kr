---
title: Rethrow 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Rethrow.UI
ms.assetid: 9cfa2eda-395f-4cf3-9154-83fadd4f7452
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 8b023a42da1c862927606c4bec0215120a5e5a11
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62937759"
---
# <a name="rethrow-activity-designer"></a>Rethrow 활동 디자이너
**Rethrow** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.Rethrow> 활동입니다.  
  
## <a name="the-rethrow-activity"></a>Rethrow 활동  
 <xref:System.Activities.Statements.Rethrow> 활동은 이전에 throw된 예외를 throw합니다. 이 활동은 <xref:System.Activities.Statements.Catch> 활동의 <xref:System.Activities.Statements.TryCatch> 처리기에서만 사용할 수 있습니다.  
  
### <a name="using-the-rethrow-activity-designer"></a>ReThrow 활동 디자이너 사용  
 **다시 Throw** 활동 디자이너에서 찾을 수 있습니다 합니다 **오류 처리** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구상자**탭의 왼쪽에는 [!INCLUDE[wfd2](../includes/wfd2-md.md)] (또는 선택 **도구 모음** 에서 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 **다시 Throw** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면 아무 곳에 나 작업은 일반적으로, 등 배치를 <xref:System.Activities.Statements.Sequence>. 이렇게를 <xref:System.Activities.Statements.Rethrow> 기본값을 사용 하 여 활동 **DisplayName** Throw입니다. <xref:System.Activities.Activity.DisplayName%2A> 헤더의 값을 편집할 수 있습니다 합니다 **다시 Throw** 활동 디자이너 또는 **DisplayName** 속성 그리드의 상자입니다.  
  
### <a name="the-rethrow-properties"></a>Rethrow 속성  
 다음 표에서는 <xref:System.Activities.Statements.Rethrow> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Rethrow> 활동의 선택적 이름을 지정합니다. 기본값은 Rethrow입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [컬렉션](../workflow-designer/collection-activity-designers.md)   
 [Throw](../workflow-designer/throw-activity-designer.md)   
 [TryCatch](../workflow-designer/trycatch-activity-designer.md)