---
title: '워크플로 디자이너: 활동 대리자 정의 및 사용'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 34cb06bbc5c9575f5a10507a8015c9819e7b533b
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66431789"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>방법: 워크플로 디자이너에서 활동 대리자 정의 및 사용

.NET framework 4.5에 대 한 기본 제공 디자이너를 포함 합니다 <xref:System.Activities.Statements.InvokeDelegate> 활동입니다. 이 디자이너는 <xref:System.Activities.ActivityDelegate> 또는 <xref:System.Activities.ActivityAction> 같은 <xref:System.Activities.ActivityFunc%601>에서 파생되는 작업에 대리자를 할당하는 데 사용할 수 있습니다.

## <a name="define-an-activity-delegate"></a>작업 대리자 정의

1. 새 **워크플로 콘솔 응용 프로그램** 프로젝트입니다.

   > [!NOTE]
   > 표시 되지 않는 경우는 **워크플로** 템플릿 프로젝트를 먼저 설치 합니다 **Windows Workflow Foundation** Visual Studio의 구성 요소입니다. 자세한 지침은 [Windows Workflow Foundation 설치](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)합니다.

3. 프로젝트를 마우스 오른쪽 단추로 클릭 **솔루션 탐색기** 선택한 **추가** > **새 항목**합니다. 선택 된 **워크플로** 범주를 선택한 후는 **활동** 항목 템플릿. 새 활동 이름을 **MyForEach.xaml** 선택한 후 **확인**합니다.

   활동이는 워크플로 디자이너에서 열립니다.

4. 워크플로 디자이너에서을 클릭 합니다 **인수** 탭 합니다.

5. 클릭 **인수를 만드는**합니다. 새 인수의 이름을 **항목**합니다.

6. 에 **인수 형식** 열 선택 **Array of [T]** 합니다.

7. 형식 브라우저에서 선택 **개체** 선택한 후 **확인**합니다.

8. 클릭 **만드는 인수** 다시 합니다. 새 인수의 이름을 **본문**합니다. 에 **방향을** 선택 새 인수에 대 한 열 **속성**합니다.

9. 인수 형식 열에서 선택 **형식 찾아보기**

10. 형식 브라우저에 입력 **ActivityAction** 에 **형식 이름을** 필드입니다. 선택 **ActivityAction\<T >** 트리 보기에서. 선택 **개체** 형식에 할당할 나타나는 드롭다운에서 **ActivityAction\<개체 >** 인수입니다.

11. 끌어서를 <xref:System.Activities.Statements.While> 에서 작업 합니다 **제어 흐름** 디자이너 화면에 도구 상자의 섹션입니다.

12. 선택 합니다 <xref:System.Activities.Statements.While> 작업과 선택 합니다 **변수** 탭 합니다.

13. 선택 **변수를 만듭니다**합니다. 새 변수의 이름을 **인덱스**합니다.

14. 에 **변수 형식** 열 선택 **Int32**합니다. 유지 된 **범위** 으로 **하는 동안**, 및 **기본** 열은 비워 둠.

15. 설정 합니다 **조건** 의 속성을 <xref:System.Activities.Statements.While> 활동을 **인덱스 < Items.Length;** .

16. 끌어서는 <xref:System.Activities.Statements.InvokeDelegate> 활동에서를 **기본** 에 도구 상자의 섹션을 **본문** 의 <xref:System.Activities.Statements.While> 활동입니다.

17. 선택 **본문** 대리자 드롭다운 목록에서.

18. 에 **속성** 그리드를 <xref:System.Activities.Statements.InvokeDelegate> 활동을 클릭는 **...**  단추를 **대리자 인수** 속성입니다.

19. 에 **값** 명명 된 인수의 열 **인수**를 입력 **Items [Index]** 합니다. 클릭 **확인** 닫으려면 합니다 **DelegateArguments** 대화 합니다.

20. <xref:System.Activities.Statements.Assign> 활동을 <xref:System.Activities.Statements.InvokeDelegate> 활동 아래의 가로선으로 끌어 놓습니다. <xref:System.Activities.Statements.Assign> 활동을 만든 및 <xref:System.Activities.Statements.Sequence> 활동에 두 활동을 포함 하도록 자동으로 만들어집니다는 **본문** 섹션을 **MyForEach** 활동. 이후에 시퀀스는 필요 합니다 **본문** 섹션에는 단일 활동만 포함할 수 있습니다. 자동으로 새로 만들 <xref:System.Activities.Statements.Sequence> 활동은.NET Framework 4.5의 새로운 기능입니다.

21. 설정를 **에** 의 속성을 <xref:System.Activities.Statements.Assign> 활동을 **인덱스**합니다. 설정를 **값** 의 속성을 **할당** 활동을 **index+1**합니다.

    사용자 지정 **MyForEach** 를 통해 전달 되는 각 값에 한 번씩 임의의 활동을 호출 하는 활동을 **항목** 활동에 대 한 입력으로 컬렉션의 값을 사용 하 여 컬렉션입니다.

## <a name="use-the-custom-activity-in-a-workflow"></a>워크플로에서 사용자 지정 활동 사용

1. 키를 눌러 프로젝트를 빌드할 **Ctrl**+**Shift**+**B**합니다.

2. **솔루션 탐색기**오픈 **Workflow1.xaml** 디자이너에서 합니다.

3. 끌어서를 **MyForEach** 활동을 도구 상자에서 디자이너 화면으로 합니다. 작업은 프로젝트와 동일한 이름 사용 하 여 도구 상자의 섹션.

4. 설정 합니다 **항목** 의 속성을 **MyForEach** 활동을 **new Object {1, "abc"}** .

5. 끌어서를 <xref:System.Activities.Statements.WriteLine> 활동에서를 **기본** 에 도구 상자의 섹션을 **Delegate: Body** 섹션을 **MyForEach** 활동입니다.

6. 설정 합니다 **텍스트** 의 속성을 <xref:System.Activities.Statements.WriteLine> 활동을 **argument.tostring ()** .

워크플로가 실행 되 면 다음 출력이 콘솔에 표시:

**1**
**abc**