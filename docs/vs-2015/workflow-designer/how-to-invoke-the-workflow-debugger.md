---
title: 'How to: Invoke the Workflow Debugger | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 13fd54eeebf0323fcb9b8cad6a8cd8b75ae11fb3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292894"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>방법: 워크플로 디버거 호출
일반적으로 워크플로 디버깅은 다른 Visual Studio 프로그래밍 언어로 작성된 프로그램의 디버깅과 동일합니다. 다음과 같은 방법으로 워크플로 디버거를 시작할 수 있습니다.

- Select **Attach to Process** on the **Debug** menu to select the running host process for your workflow instance. 이 절차는 관리 코드의 호스트 프로세스에 연결하는 절차와 동일합니다.

- Press **F5** to start running an instance of the workflow, or to continue to run after a breakpoint has been hit.

- 원격 디버깅을 사용합니다. For information on using remote debugging, see [How to: Enable Remote Debugging](https://go.microsoft.com/fwlink/?LinkId=196257).

    > [!NOTE]
    > If the workflow application targets the x86 architecture and is hosted on a machine running a 64 bit operating system, then remote debugging will not work unless [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] is installed on the remote machine or the target for the workflow application is changed to **Any CPU**.

### <a name="stepping-through-code"></a>단계별 코드 실행

- **Step In**: You can step into an activity using **F11**. 디버거는 정의된 임의의 처리기에서 한 단계씩 코드를 실행합니다. 정의된 처리기가 없으면 해당 활동을 프로시저 단위로 실행합니다. 다른 활동이 포함된 복합 활동의 경우 실행 중인 첫 번째 활동을 단계적으로 실행합니다.

- **Step Out:** You can step out of an activity using **Shift-F11**. 활동에서 나가기를 수행하면 현재 활동 및 모든 형제 활동이 완료 시까지 실행됩니다. 그런 다음 디버거는 현재 활동의 부모에서 중단합니다. 코드 처리기에서 나갈 때 디버거는 처리기가 연결된 활동에서 중단합니다.

- **Step Over**: You can step over an activity using **F10**. 복합 활동을 프로시저 단위로 실행할 때 디버거는 복합 활동의 첫 번째 실행 가능 자식에서 중단합니다. <xref:System.Activities.Statements.Assign> 활동과 같은 비복합 활동을 프로시저 단위로 실행할 경우 디버거는 해당 활동 및 그와 연결된 처리기를 실행하고 다음 활동에서 중단합니다. 실행할 활동이 복합 활동 중 마지막 자식 활동인 경우, 디버거는 활동 실행 후 부모 활동에서 중단합니다.

### <a name="debugging-with-f5"></a>F5 키를 사용한 디버깅

- If you are building a Workflow Console Application project, simply press **F5** to begin debugging into your application and workflow. 활동 라이브러리를 자체적으로 빌드하려는 경우 시작 프로젝트인 실행 가능 호스트 애플리케이션이 있어야 합니다. To set a startup project in **Solution Explorer**, right-click the project name of the host and select **Set as StartUp Project**.

## <a name="see-also"></a>관련 항목:
 [How to: Set Breakpoints in Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md) [Debugging Workflows with the Workflow Designer](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)