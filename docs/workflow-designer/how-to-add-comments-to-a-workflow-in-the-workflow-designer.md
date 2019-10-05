---
title: '워크플로 디자이너-방법: 워크플로에 주석 추가'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: c7eb15c6d19ab40df6913dd67466dc20012492b7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62950374"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>방법: 워크플로 디자이너에서 워크플로에 주석 추가

.NET Framework 4.5 큰 규모의 더 복잡 한 워크플로 만들기를 용이 하 게 다음과 같은 유형의 디자이너에서 항목에 주석을 추가 하는 개발자를 허용 합니다.

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- <xref:System.Activities.Statements.FlowNode>에서 파생된 클래스

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> 주석 내용은 워크플로와 관련된 XAML 파일에 일반 텍스트로 저장되며 다른 사용자가 읽을 수 있습니다. 민감한 정보를 주석에 입력할 때는 주의하세요.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>디자이너의 활동에 주석 추가

1. 워크플로 디자이너에서 마우스 오른쪽 단추로 클릭 워크플로 디자이너 및 선택 항목이 **주석을**를 **주석 추가**합니다.

1. 제공된 공란에 주석 텍스트를 추가합니다.

   항목에 주석 아이콘이 표시 됩니다. 주석 아이콘을 가리키면 주석 텍스트를 표시 합니다.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>활동 디자이너에 주석 표시

1. 활동 외부에 표시 하는 주석이 있는 활동 디자이너를 사용 하 여 클릭 합니다 **Pin** 에서 주석 표시기의 아이콘입니다.

   주석은 활동 디자이너에 표시 됩니다. 아래의 스크린샷에서 활동 디자이너에 "워크플로에서 활동 시작" 주석이 표시됩니다.

   ![활동 디자이너에 표시되는 주석](../workflow-designer/media/annotationindesigner.png)

2. 활동 디자이너 외부에 주석을 표시할 활동 디자이너의 주석 영역을 마우스로 클릭 합니다 **고정 해제** 아이콘

   ![활동 디자이너 외부에 표시 되는 주석](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>모든 주석 표시 또는 숨기기

1. 주석이 있는 활동을 마우스 오른쪽 단추로 클릭합니다. 선택 **주석을**하십시오 **대 한 모든 주석 표시**.

   모든 주석이 활동 디자이너에 표시 됩니다.

1. 활동 디자이너 외부 대 한 모든 주석으로 표시 하려면 마우스 오른쪽 단추로 클릭 선택한 활동 **주석을**를 **모든 주석 숨기기**합니다.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>활동 주석 편집 또는 삭제

1. 주석이 있는 활동을 마우스 오른쪽 단추로 클릭합니다.

1. 선택 **주석을**를 **주석 편집** 하거나 **주석 삭제**합니다.

   주석 편집을 위해 열려 되었거나 삭제 되었습니다.

1. 워크플로 디자이너 및 select를 마우스 오른쪽 단추로 클릭 한 번에 모든 주석을 삭제할 **주석**를 **모든 주석을 삭제**합니다.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>변수 또는 인수에 대한 주석 추가, 편집 및 삭제

1. 변수 또는 인수를 마우스 오른쪽 단추로 클릭하고 주석 추가를 선택합니다.

1. 주석의 텍스트를 입력합니다. 변수 또는 인수에 주석 아이콘이 표시 됩니다.

1. 주석이 있는 변수 또는 인수를 마우스 오른쪽 단추로 클릭합니다. 주석 편집을 선택합니다.

   주석 편집을 위해 열려 있습니다.

1. 주석이 있는 변수 또는 인수를 마우스 오른쪽 단추로 클릭합니다. 주석 삭제를 선택합니다.

   주석이 삭제 됩니다.