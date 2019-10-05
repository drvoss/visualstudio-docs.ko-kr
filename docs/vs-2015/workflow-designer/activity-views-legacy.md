---
title: 활동 뷰 (레거시) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- activities, activity views
- views, activity
- activity views
ms.assetid: 83dc68cd-2cb2-45c2-9a6e-10d82053171a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 62b3c9185226512ff28c8d028cd0ba7d33b0f12f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977448"
---
# <a name="activity-views-legacy"></a>활동 뷰(레거시)
[!INCLUDE[wf](../includes/wf-md.md)]에서 제공하는 많은 활동은 워크플로를 구성하는 데 사용되며 이러한 활동에는 레거시 [!INCLUDE[wfd1](../includes/wfd1-md.md)]에서 사용할 수 있는 몇 가지 디자인 뷰가 있습니다. 활동 디자이너를 끌어다 놓으면 합니다 **도구 상자** 디자인 화면으로 이동 하 고 그 후 작업을 선택할 때마다 사용 하 여 다른 디자인 뷰 간을 전환할 수 있습니다는 **워크플로**메뉴 또는 선택된 된 작업을 마우스 오른쪽 단추로 클릭 합니다. 또한 선택된 항목의 이름 위로 포인터를 옮기면 드롭다운 탭 집합이 나타나 여러 뷰 사이를 전환할 때 사용할 수 있습니다.  
  
 모든 활동에는 하나 이상의 보기; 이 활동 디자이너를 끌어다 놓으면 표시 된 기본 보기는 **도구 상자** 디자인 화면으로 합니다. 이 활동 기본 뷰 제품은 합니다 **[활동 유형] 보기** 옵션 메뉴 및 탭, 예를 들어 **병렬 보기**합니다. 대부분의 활동에 추가 뷰가 있으며, 활동마다 서로 다른 뷰를 가질 수 있습니다. 예를 들어 합니다 [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093) 활동은 보정 뷰 및 [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030) 활동에는 이벤트 보기. Windows Workflow Foundation에서 제공 하는 활동 중 상당수에 **취소 처리기 보기** 및 **보기 오류** 보기에는 뷰를 디자인 합니다 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) 와 [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) 상호 연결 합니다.  
  
 다음 표에서는 각 뷰의 이름과 설명을 보여 줍니다.  
  
|메뉴/탭 옵션|설명|  
|----------------------|-----------------|  
|**[활동 유형] 보기**|선택한 활동의 기본 그래픽 표현을 보려면 이 메뉴 또는 탭 옵션을 선택합니다.|  
|**취소 처리기 보기**|이 메뉴 또는 탭 옵션 뷰를 선택 합니다 [CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050) 사용 하면 선택한 활동과 연결 합니다.|  
|**오류 처리기 보기**|이 메뉴 또는 탭 옵션 뷰를 선택 합니다 [FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055) 사용 하면 선택한 활동과 연결 합니다.|  
|**보정 핸들러 보기**|이 메뉴 또는 탭 옵션 뷰를 선택 합니다 [CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053) 선택한 내용과 연관 [TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)합니다.|  
|**이벤트 핸들러 보기**|이 메뉴 또는 탭 옵션 뷰를 선택 합니다 [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018) 선택한 내용과 연관 된 [EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)합니다.|  
  
 유사한 뷰에 대 한 자세한 내용은 [순차 워크플로 뷰 (레거시)](../workflow-designer/sequential-workflow-views-legacy.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [레거시 워크플로 활동](../workflow-designer/legacy-workflow-activities.md)   
 [순차 워크플로 뷰(레거시)](../workflow-designer/sequential-workflow-views-legacy.md)