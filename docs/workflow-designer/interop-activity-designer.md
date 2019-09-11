---
title: 워크플로 디자이너에서 Interop 활동 디자이너
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 688ef92fae5bd0cbaa5ddc653bbaab5692f4827f
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747142"
---
# <a name="interop-activity-designer"></a>Interop 활동 디자이너

합니다 **Interop** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.Interop> 활동입니다.

## <a name="the-interop-activity"></a>Interop 활동

<xref:System.Activities.Statements.Interop> 활동은 워크플로의 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName>에서 파생되는 형식의 실행을 관리합니다.

### <a name="use-the-interop-activity-designer"></a>Interop 활동 디자이너 사용

**Interop** 활동 디자이너에서 찾을 수 있습니다 합니다 **마이그레이션** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구상자**탭 합니다. 또는 선택할 **도구 상자** 에서 합니다 **뷰** 메뉴 또는 키를 눌러 **Ctrl**+**Alt** + **X**합니다.

합니다 [마이그레이션](../workflow-designer/migration-activity-designers.md) 포함 된 범주를 <xref:System.Activities.Statements.Interop> 활동에만 나타납니다 **도구 상자** 프로젝트 대상이.NET Framework 4 (전체) 경우 이상. 경우 필요에 따라 변경할 수 있습니다 프레임 워크 버전을 하는 프로젝트의 대상이 됩니다.

합니다 **Interop** 활동 디자이너에서 끌 수 있습니다 **도구 상자** 작업은 일반적으로, 등 배치 때마다 워크플로 디자이너 화면에 놓여진 및는 <xref:System.Activities.Statements.Sequence>합니다. 삭제 된 **Interop** 활동 디자이너를 만듭니다를 <xref:System.Activities.Statements.Interop> 기본값을 사용 하 여 활동 **DisplayName** Interop의 합니다. 편집할 수 있습니다는 <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에는 **Interop** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자입니다.

클릭 합니다 **찾아보려면 클릭** 에서 텍스트를 **ActivityType** 상자에서를 **Interop** 활동 디자이너나 속성 표의 열에 **찾아보기 및 선택 된.Net 형식** 대화 상자. 워크플로 3.0 또는 워크플로 3.5 활동에 대 한 형식만 표시 됩니다. 즉,에서 파생 된 형식만 <xref:System.Workflow.ComponentModel.Activity> 표시 됩니다. 이 상자를 사용 하 여 형식을 지정 하는 방법에 대 한 자세한 내용은 참조 하세요. [찾아.NET 유형 선택 대화 상자](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md)합니다.

### <a name="the-interop-properties"></a>Interop 속성

다음 표는 <xref:System.Activities.Statements.Interop> 속성을 디자이너에서 사용 되는 방법을 설명 합니다. 속성 표에서 또는 워크플로 디자이너 화면에서 이러한 속성을 편집할 수 있습니다.

|속성 이름|필수|사용|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> 활동의 이름입니다. 기본값은 **Interop**합니다. 표시 이름에 필요 하지는 않지만 것이 좋습니다 하나를 제공 합니다.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|<xref:System.Activities.Statements.Interop> 활동에 포함된 활동의 형식을 지정합니다. 지정된 이 형식은 <xref:System.Workflow.ComponentModel.Activity>에서 파생된 것이어야 합니다.|

## <a name="see-also"></a>참고자료

- [마이그레이션](../workflow-designer/migration-activity-designers.md)