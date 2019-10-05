---
title: Interop 활동 디자이너 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55829e85b17bcdc70e419a8496d4756d0acb4a56
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952050"
---
# <a name="interop-activity-designer"></a>Interop 활동 디자이너
합니다 **Interop** 활동 디자이너는 만들기 및 구성 하는 데 사용 되는 <xref:System.Activities.Statements.Interop> 활동입니다.  
  
## <a name="the-interop-activity"></a>Interop 활동  
 <xref:System.Activities.Statements.Interop> 활동은 워크플로의 <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName>에서 파생되는 형식의 실행을 관리합니다.  
  
### <a name="using-the-interop-activity-designer"></a>Interop 활동 디자이너 사용  
 **Interop** 활동 디자이너에서 찾을 수 있습니다 합니다 **마이그레이션** 범주의 **도구 상자**를 클릭 하 여 액세스를 **도구상자**탭 (또는 선택할 **도구 상자** 에서 합니다 **보기** 메뉴 또는 CTRL + ALT + X를 누릅니다.)  
  
 [마이그레이션](../workflow-designer/migration-activity-designers.md) 포함 된 범주를 <xref:System.Activities.Statements.Interop> 활동에만 표시 합니다 **도구 상자** 프로젝트는 전체를 대상으로 하는 경우 [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)]합니다.  
  
 C# 프로젝트 대상을 조정할 수 있습니다 전체를 사용 하도록 프로젝트 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 에서 프로젝트를 마우스 오른쪽 단추로 클릭 합니다 **솔루션 탐색기** 를 선택 하 고 **속성**합니다. 에 **응용 프로그램** 탭을 선택 합니다 **.NET Framework 4** 옵션을 **대상 프레임 워크**. 선택 된 **예** 단추를 **대상 프레임 워크 변경** 이 변경 내용을 확인 하 라는 메시지가 표시 하는 대화 상자.  
  
 VB 프로젝트 대상을 조정할 수 있습니다 전체를 사용 하도록 프로젝트 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 에서 프로젝트를 마우스 오른쪽 단추로 클릭 합니다 **솔루션 탐색기** 를 선택 하 고 **속성**합니다. 에 **컴파일할** 탭을 클릭 합니다 **고급 컴파일 옵션** 단추입니다. 선택 **.NET Framework 4** 에서 합니다 **대상 프레임 워크 목록** 을 클릭 한 다음 **확인**합니다. 클릭 합니다 **예** 단추를 **대상 프레임 워크 변경** 이 변경 내용을 확인 하 라는 메시지가 표시 하는 대화 상자.  
  
 **Interop** 활동 디자이너에서 끌 수 있습니다 합니다 **도구 상자** 삭제에 및를 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면 아무 곳에 나 작업은 일반적으로, 등 배치를 <xref:System.Activities.Statements.Sequence>. 이렇게를 <xref:System.Activities.Statements.Interop> 기본값을 사용 하 여 활동 **DisplayName** Interop입니다. <xref:System.Activities.Activity.DisplayName%2A> 의 헤더에서 편집할 수 있습니다 합니다 **Interop** 활동 디자이너 또는 합니다 **DisplayName** 속성 그리드의 상자.  
  
 클릭 된 **찾아보려면 클릭...** 텍스트를 **ActivityType** 상자에서를 **Interop** 활동 디자이너나 속성 표의 불러오려면를 **형식 찾아보기 및 선택.Net** 대화 상자. 워크플로 3.0 또는 워크플로 3.5 활동의 형식(<xref:System.Workflow.ComponentModel.Activity>에서 파생된 형식)만 표시됩니다. [!INCLUDE[crabout](../includes/crabout-md.md)] 이 상자를 사용 하 여 형식을 지정 하는 [찾아.NET 유형 선택 대화 상자](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) 항목입니다.  
  
### <a name="the-interop-properties"></a>Interop 속성  
 다음 표에서는 <xref:System.Activities.Statements.Interop> 속성을 보여 주고 디자이너에서 이 속성을 사용하는 방법을 설명합니다. 이러한 속성은 속성 표 또는 [!INCLUDE[wfd2](../includes/wfd2-md.md)] 화면에서 편집할 수 있습니다.  
  
|속성 이름|필수|사용|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.Interop> 활동의 이름입니다. 기본값은 Interop입니다. 표시 이름이 꼭 필요하지 않더라도 표시 이름을 사용하는 것이 좋습니다.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|<xref:System.Activities.Statements.Interop> 활동에 포함된 활동의 형식을 지정합니다. 지정된 이 형식은 <xref:System.Workflow.ComponentModel.Activity>에서 파생된 것이어야 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [마이그레이션](../workflow-designer/migration-activity-designers.md)