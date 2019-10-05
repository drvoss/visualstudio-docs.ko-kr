---
title: '방법: 워크플로 디자이너에서 활동 대리자 정의 및 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 37adb6cf6462887010b1c06c7d5af4a539203b15
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62974581"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>방법: 워크플로 디자이너에서 활동 대리자 정의 및 사용
[!INCLUDE[net_v45](../includes/net-v45-md.md)]에서는 <xref:System.Activities.Statements.InvokeDelegate> 작업에 대해 기본으로 제공되는 새 디자이너를 포함하고 있습니다. 이 디자이너는 <xref:System.Activities.ActivityDelegate> 또는 <xref:System.Activities.ActivityAction> 같은 <xref:System.Activities.ActivityFunc%601>에서 파생되는 작업에 대리자를 할당하는 데 사용할 수 있습니다.  
  
### <a name="define-an-activity-delegate"></a>작업 대리자 정의  
  
1. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]을 선택 **파일**를 **새로 만들기**를 **프로젝트**합니다. 선택 된 **워크플로** 왼쪽의 노드 및 **워크플로 콘솔 응용 프로그램** 오른쪽에서 템플릿. 원하는 경우 프로젝트 이름을 지정 하 고 클릭 **확인**합니다.  
  
2. 프로젝트를 마우스 오른쪽 단추로 클릭 **솔루션 탐색기** 선택한 **추가**, **새 항목...** . 선택 합니다 **워크플로** 왼쪽에 노드 및 **활동** 오른쪽에서 템플릿. 새 활동 이름을 **MyForEach.xaml** 누릅니다 **확인**합니다. Workflow Designer에서 활동이 열립니다.  
  
3. 워크플로 디자이너에서을 클릭 합니다 **인수** 탭 합니다.  
  
4. 클릭 **인수를 만드는**합니다. 새 인수의 이름을 **항목**합니다.  
  
5. 에 **인수 형식** 열 선택 **Array of [T]** 합니다.  
  
6. 형식 브라우저에서 선택 **개체**합니다. **확인**을 클릭합니다.  
  
7. 클릭 **만드는 인수** 다시 합니다. 새 인수의 이름을 **본문**합니다. 에 **방향을** 선택 새 인수에 대 한 열 **속성**합니다.  
  
8. 인수 형식 열에서 선택 **형식 찾아보기...**  
  
9. 형식 브라우저에 입력 **ActivityAction** 에 **형식 이름을** 필드입니다. 선택 **ActivityAction\<T >** 트리 보기에서. 선택 **개체** 형식에 할당할 나타나는 드롭다운에서 **ActivityAction\<개체 >** 인수입니다.  
  
10. 끌어서를 <xref:System.Activities.Statements.While> 에서 작업 합니다 **제어 흐름** 디자이너 화면에 도구 상자의 섹션입니다.  
  
11. 선택 합니다 <xref:System.Activities.Statements.While> 작업과 선택 합니다 **변수** 탭 합니다.  
  
12. 선택 **변수를 만듭니다**합니다. 새 변수의 이름을 **인덱스**합니다.  
  
13. 에 **변수 형식** 열 선택 **Int32**합니다. 유지 된 **범위** 으로 **하는 동안**, 및 **기본** 열은 비워 둠.  
  
14. 설정 합니다 **조건** 의 속성을 <xref:System.Activities.Statements.While> 활동을 **인덱스 < Items.Length;**.  
  
15. 끌어서는 <xref:System.Activities.Statements.InvokeDelegate> 활동에서를 **기본** 에 도구 상자의 섹션을 **본문** 의 <xref:System.Activities.Statements.While> 활동입니다.  
  
16. 선택 **본문** 대리자 드롭다운 목록에서.  
  
17. 에 **속성** 그리드를 <xref:System.Activities.Statements.InvokeDelegate> 활동을 클릭는 **...** 단추는 **대리자 인수** 속성입니다.  
  
18. 에 **값** 명명 된 인수의 열 **인수**를 입력 **Items [Index]** 합니다. 클릭 **확인** 닫으려면 합니다 **DelegateArguments** 대화 합니다.  
  
19. <xref:System.Activities.Statements.Assign> 활동을 <xref:System.Activities.Statements.InvokeDelegate> 활동 아래의 가로선으로 끌어 놓습니다. <xref:System.Activities.Statements.Assign> 활동 생성 될 및 <xref:System.Activities.Statements.Sequence> 활동에 두 활동을 포함 하도록 자동으로 생성 됩니다는 **본문** 섹션의 **MyForEach** 활동. 이후에 시퀀스는 필요 합니다 **본문** 섹션에는 단일 활동만 포함할 수 있습니다. 새 <xref:System.Activities.Statements.Sequence> 활동을 자동으로 만드는 기능은 [!INCLUDE[net_v45](../includes/net-v45-md.md)]의 새 기능입니다.  
  
20. 설정를 **에** 의 속성을 <xref:System.Activities.Statements.Assign> 활동을 **인덱스**합니다. 설정를 **값** 의 속성을 **할당** 활동을 **index+1**합니다.  
  
    사용자 지정 **MyForEach** 활동에는 임의의 활동을 통해 전달 된 각 값에 한 번씩 호출 이제 합니다 **항목** 활동에 대 한 입력으로 컬렉션의 값을 사용 하 여 컬렉션입니다.  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>워크플로에서 사용자 지정 활동 사용  
  
1. 키를 눌러 프로젝트를 빌드할 **Ctrl + Shift + B**합니다.  
  
2. **솔루션 탐색기**오픈 **Workflow1.xaml** 디자이너에서 합니다.  
  
3. 끌어서를 **MyForEach** 활동을 도구 상자에서 디자이너 화면으로 합니다. 활동은 프로젝트와 같은 이름을 사용하여 도구 상자의 한 섹션에 있게 됩니다.  
  
4. 설정 합니다 **항목** 의 속성을 **MyForEach** 활동을 **new Object {1, "abc"}**.  
  
5. 끌어서를 <xref:System.Activities.Statements.WriteLine> 활동에서를 **기본** 에 도구 상자의 섹션을 **Delegate: Body** 섹션을 **MyForEach** 활동입니다.  
  
6. 설정 합니다 **텍스트** 의 속성을 <xref:System.Activities.Statements.WriteLine> 활동을 **argument.tostring ()**.  
  
   워크플로가 실행되면 콘솔에 다음이 표시됩니다.  
  
   **1**   
   **abc**