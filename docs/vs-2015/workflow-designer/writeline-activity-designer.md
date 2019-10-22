---
title: WriteLine 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.WriteLine.UI
ms.assetid: 1b5f29a8-b7fd-477e-949e-2f689cae3c96
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c4f656578526879774e698523239d5a9b2b14ccd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657523"
---
# <a name="writeline-activity-designer"></a>WriteLine 활동 디자이너
**WriteLine** 활동 디자이너는 <xref:System.Activities.Statements.WriteLine> 활동을 만들고 구성 하는 데 사용 됩니다.

## <a name="the-writeline-activity"></a>WriteLine 활동
 <xref:System.Activities.Statements.WriteLine> 활동은 지정된 <xref:System.IO.TextWriter> 개체에 텍스트를 씁니다. 지정된 <xref:System.IO.TextWriter>가 없는 경우 <xref:System.Activities.Statements.WriteLine>은 콘솔에 텍스트를 씁니다.

### <a name="using-the-writeline-activity-designer"></a>WriteLine 활동 디자이너 사용
 **WriteLine** 활동 디자이너는 **도구**상자의 **기본 형식** 범주에 있습니다 .이 범주에 액세스 하려면 [!INCLUDE[wfd2](../includes/wfd2-md.md)]의 **도구 상자** 탭을 클릭 하거나, **보기** 메뉴에서 **도구 모음** 을 선택 하거나, CTRL + ALT + X)

 **WriteLine** 활동 디자이너를 **도구 상자** 에서 끌어와 같이 일반적으로 활동을 <xref:System.Activities.Statements.Sequence> 배치 하는 아무 곳에 나 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면에 놓을 수 있습니다. 그러면 기본 <xref:System.Activities.Statements.WriteLine>인 WriteLine이라는 이름의 <xref:System.Activities.Activity.DisplayName%2A> 활동이 만들어집니다. 이 <xref:System.Activities.Activity.DisplayName%2A>는 **WriteLine** 활동 디자이너의 머리글 또는 속성 표의 **DisplayName** 상자에서 편집할 수 있습니다.

### <a name="the-writeline-properties"></a>WriteLine 속성
 다음 표에서는 <xref:System.Activities.Statements.WriteLine> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표에서 편집할 수 있으며 일부 속성은 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 디자이너 화면에서 편집할 수 있습니다.

|속성 이름|필요한 공간|사용 현황|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.WriteLine> 활동의 이름입니다. 기본값은 WriteLine입니다. <xref:System.Activities.Activity.DisplayName%2A>은 꼭 필요하지 않더라도 사용하는 것이 좋습니다.|
|<xref:System.Activities.Statements.WriteLine.Text%2A>|False|쓸 텍스트입니다. 속성을 설정 하려면 **WriteLine** 활동 디자이너의 **텍스트** 상자 또는 속성 표에 Visual Basic 식을 입력 합니다.|
|<xref:System.Activities.Statements.WriteLine.TextWriter%2A>|False|<xref:System.IO.TextWriter>이 <xref:System.Activities.Statements.WriteLine>를 쓸 대상 <xref:System.Activities.Statements.WriteLine.Text%2A>입니다. 기본값은 콘솔입니다.|

## <a name="see-also"></a>관련 항목:
 [기본 형식](../workflow-designer/primitives-activity-designers.md) [할당](../workflow-designer/assign-activity-designer.md) [지연](../workflow-designer/delay-activity-designer.md) [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)