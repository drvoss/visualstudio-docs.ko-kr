---
title: 작업 창 사용 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa59e1e57750c9c2075c10c76ab5c518ed0e8686
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793908"
---
# <a name="using-the-tasks-window"></a>작업 창 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**태스크** 창은 합니다 **스레드** 창에 대 한 정보를 표시 한다는 점을 제외 하 고 <xref:System.Threading.Tasks.Task?displayProperty=fullName>를 [task_handle](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7), 또는 [WinJS.Promise ](http://msdn.microsoft.com/library/windows/apps/br211867.aspx) 각 스레드 대신 개체입니다. 스레드와 마찬가지로, 작업은 동시에 실행할 수 있는 비동기 작업을 나타내지만 여러 작업이 같은 스레드에서 실행될 수도 있습니다. 참조 [JavaScript (Windows 스토어 앱)의 비동기 프로그래밍](http://msdn.microsoft.com/library/windows/apps/hh700330.aspx) 자세한 내용은 합니다.  
  
 관리 코드에서 사용할 수 있습니다는 **태스크** 창을 사용 하 여 작업할 때 <xref:System.Threading.Tasks.Task?displayProperty=fullName> 개체 또는 합니다 **await** 및 **비동기** 키워드 (**Await** 하 고 **Async** VisualBasic에서). 관리 코드의 작업에 대 한 자세한 내용은 참조 하세요. [병렬 프로그래밍](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)합니다.  
  
 네이티브 코드에서 사용할 수 있습니다는 **태스크** 창을 사용 하 여 작업할 때 [작업 그룹](http://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077)를 [병렬 알고리즘](http://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [비동기 에이전트](http://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a), 및 [간단한 작업](http://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90)합니다. 네이티브 코드의 작업에 대 한 자세한 내용은 참조 하세요. [동시성 런타임](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)합니다.  
  
 JavaScript에서 promise .then 코드로 작업할 때 작업 창을 사용할 수 있습니다.  
  
 사용할 수는 **작업** 창 때마다 디버거를 중단 합니다. 에 액세스할 수 있습니다는 **디버그** 를 클릭 하 여 메뉴 **Windows** 클릭 한 다음 **작업**합니다. 다음 그림에 표시 된 **작업** 기본 모드의 창.  
  
 ![병렬 작업 창](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
>  관리 코드에서 <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.TaskStatus> 또는 <xref:System.Threading.Tasks.TaskStatus> 상태에 있는 <xref:System.Threading.Tasks.TaskStatus>는 관리되는 스레드가 대기 또는 조인 상태에 있는 경우 작업 창에 표시되지 않을 수도 있습니다.  
  
## <a name="tasks-column-information"></a>작업 열 정보  
 열에는 **작업** 창에 다음 정보를 표시 합니다.  
  
|열 이름|설명|  
|-----------------|-----------------|  
|**플래그**|플래그 설정된 작업이 표시되며 작업에 플래그를 설정하거나 해제할 수 있습니다.|  
|**아이콘**|노란색 화살표는 현재 작업을 나타냅니다. 현재 작업은 현재 스레드의 최상위 작업입니다.<br /><br /> 흰색 화살표는 중단 작업(디버거가 호출된 현재 작업)을 나타냅니다.<br /><br /> 일시 중지 아이콘은 사용자가 중지한 작업을 나타냅니다. 목록에서 작업을 마우스 오른쪽 단추로 클릭하여 작업을 중지하거나 중지된 작업을 해제할 수 있습니다.|  
|**ID**|시스템에서 제공한 작업 번호입니다. 네이티브 코드에서는 작업의 주소입니다.|  
|**Status**|작업의 현재 상태(예약됨, 활성, 교착 상태, 대기 중 또는 완료됨)입니다. 예약된 작업은 아직 실행되지 않은 작업이므로 호출 스택, 할당된 스레드 또는 관련 작업이 없습니다.<br /><br /> 활성 작업은 디버거를 시작하기 전에 코드를 실행 중이던 작업입니다.<br /><br /> 대기 중인 작업은 이벤트가 신호를 받거나, 잠금이 해제되거나, 다른 작업이 완료되기를 기다리고 있어서 차단된 작업입니다.<br /><br /> 교차 상태의 작업은 해당 스레드와 다른 스레드 간에 교착 상태가 발생한 대기 중인 작업입니다.<br /><br /> 마우스로 합니다 **상태** 셀 블록에 대 한 자세한 내용은 교착 상태 또는 대기 중인 작업에 대 한 합니다. **경고:** 는 **작업** 창에서 WCT Wait Chain Traversal ()를 지원 되는 동기화 기본 형식을 사용 하는 차단 된 작업에 대해서만 교착 상태를 보고 합니다. 예를 들어,에 대 한 교착 상태가 발생 <xref:System.Threading.Tasks.Task> 디버거 보고 WCT를 사용 하는 개체 **대기-교착 상태**합니다. 디버거 WCT를 사용 하지 않는, 동시성 런타임에서 관리 되는 작업을 교착 상태에 대 한 보고 **대기**합니다. WCT에 대 한 자세한 내용은 참조 하세요. [Wait Chain Traversal](http://msdn.microsoft.com/library/ms681622\(VS.85\).aspx)합니다.|  
|**시작 시간**|작업이 활성화된 시간입니다.|  
|**기간**|작업이 활성화된 기간(초)입니다.|  
|**완료 시간**|작업이 완료된 시간입니다.|  
|**위치**|작업의 호출 스택의 현재 위치입니다. 이 셀을 가리키면 작업에 대한 전체 호출 스택을 볼 수 있습니다. 예약된 작업의 이 열에는 값이 없습니다.|  
|**Task**|작업이 생성될 때 작업으로 전달된 초기 메서드와 인수입니다.|  
|**부모**|이 작업을 만든 작업의 ID입니다. 비어 있으면 작업에 부모가 없는 것입니다. 관리되는 프로그램에만 적용됩니다.|  
|**스레드 할당**|작업이 실행 중인 스레드의 ID 및 이름입니다.|  
|**반환 상태**|작업이 완료되었을 때의 상태입니다. 반환 상태 값은 **성공을**, **Cancelled**, 및 **오류**합니다.|  
|**AppDomain**|관리 코드의 경우 작업이 실행되고 있는 응용 프로그램 도메인입니다.|  
|**task_group**|네이티브 코드의 주소에 대 한 합니다 [task_group](http://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) 개체 작업을 예약 합니다. 비동기 에이전트 및 간단한 작업의 경우 이 열은 0으로 설정됩니다.|  
|프로세스|작업이 실행 중인 프로세스의 ID입니다.|  
|비동기 상태|관리 코드의 경우 작업 상태입니다. 기본적으로 이 열은 숨겨집니다. 이 열을 표시하려면 열 머리글 중 하나에 대한 상황에 맞는 메뉴를 엽니다. 선택할 **열**하십시오 **AsyncState**합니다.|  
  
 열 머리글을 마우스 오른쪽 단추로 클릭하고 원하는 열을 선택하여 뷰에 추가할 수 있습니다. 열을 제거하려면 선택을 취소합니다. 또한 왼쪽이나 오른쪽으로 끌어서 열을 다시 정렬할 수도 있습니다. 열 바로 가기 메뉴가 다음 그림에 표시됩니다.  
  
 ![병렬 작업 창의 바로 가기 뷰 메뉴](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>작업 정렬  
 열 조건으로 작업을 정렬하려면 열 머리글을 클릭합니다. 예를 들어,를 클릭 하 여 합니다 **ID** 열 머리글을 작업 ID로 작업을 정렬할 수 있습니다: 1,2,3,4,5 등에입니다. 정렬 순서를 반대로 바꾸려면 열 머리글을 다시 클릭합니다. 현재 정렬 열과 정렬 순서는 열에 화살표로 표시됩니다.  
  
## <a name="grouping-tasks"></a>작업 그룹화  
 목록 뷰에서 열을 기준으로 작업을 그룹화할 수 있습니다. 마우스 오른쪽 단추로 클릭 하 여 예를 들어 합니다 **상태** 열 머리글을 클릭 한 다음 **상태별으로 그룹화**, 동일한 상태에 있는 모든 작업을 그룹화 할 수 있습니다. 예를 들어, 대기 중인 작업만 빨리 확인하여 차단된 이유를 살펴볼 수 있습니다. 또한 디버그 세션 중에 관심 없는 그룹을 축소할 수도 있습니다. 동일한 방식으로 다른 열을 기준으로 그룹화할 수 있습니다. 그룹 머리글 옆의 단추를 클릭하여 간단하게 그룹에 플래그를 설정하거나 해제할 수 있습니다. 다음 그림에 표시 된 **작업** 그룹화 된 모드의 창.  
  
 ![병렬 작업 창의 그룹화 된 모드](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>부모 자식 뷰  
 이 뷰는 관리 코드에서만 사용할 수 있습니다. 열 머리글을 마우스 오른쪽 단추로 클릭 한 다음 클릭 하 여 **부모 자식 뷰**, 모든 자식에서 작업은 표시 하거나 부모에서 숨길 수 있는 하위 노드입니다 계층적 보기를 작업의 목록을 변경할 수 있습니다. 다음 그림은 부모 자식 뷰의 작업을 보여 줍니다.  
  
 ![부모&#45;병렬 작업 창의 자식 뷰](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>작업에 플래그 설정  
 작업 태스크를 선택 하 여 실행 되는 작업 목록 항목을 선택 하는 스레드에 플래그를 수 **플래그** 상황에 맞는 메뉴 또는 첫 번째 열에서 플래그 아이콘을 클릭 하 여 합니다. 여러 작업에 플래그를 설정하는 경우 플래그 설정된 작업에만 초점을 맞출 수 있도록 플래그 설정된 모든 작업을 맨 위로 오게 플래그 열을 정렬할 수 있습니다. 사용할 수도 있습니다는 **병렬 스택** 만 플래그가 지정 된 작업을 보려면 창입니다. 이렇게 하면 디버깅 중 관심 없는 작업을 필터링할 수 있습니다. 플래그는 디버깅 세션 간에 유지되지 않습니다.  
  
## <a name="freezing-and-thawing-tasks"></a>작업 중지 및 재개  
 작업 목록 항목을 마우스 오른쪽 단추로 클릭 한 다음 클릭 하 여 실행 되는 작업 스레드를 중지할 수 있습니다 **할당 된 스레드 중지**합니다. (작업을 이미 중지 하는 경우 명령입니다 **할당 된 스레드 재개**.) 스레드를 중지하면 현재 중단점 이후에 코드를 단계별로 실행할 때 해당 스레드가 실행되지 않습니다. 합니다 **이 모든 스레드 중지 하지만** 명령은 작업 목록 항목을 실행 하는 것을 제외한 모든 스레드를 중지 합니다.  
  
 다음 그림에서는 각 작업에 대한 다른 메뉴 항목을 보여 줍니다.  
  
 ![병렬 작업 창의 바로 가기 스레드 메뉴](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>참고 항목  
 [Debugger Basics](../debugger/debugger-basics.md) (디버거 기본 사항)  
 [Debugging Managed Code](../debugger/debugging-managed-code.md) (관리 코드 디버그)  
 [병렬 프로그래밍](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [동시성 런타임](http://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [병렬 스택 창 사용](../debugger/using-the-parallel-stacks-window.md)   
 [연습: 병렬 응용 프로그램 디버그](../debugger/walkthrough-debugging-a-parallel-application.md)



