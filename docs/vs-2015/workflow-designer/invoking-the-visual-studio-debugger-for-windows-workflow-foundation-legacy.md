---
title: Debugger for Windows Workflow Foundation (레거시)를 호출 합니다. | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- stepping
- Step Over command
- stepping, commands
- debugging, using workflow debugger
- workflows, debugger
- workflow debugger, starting
- Step In command
- debugger, workflow
- Step Out command
- debugging workflows, starting the debugger
ms.assetid: d6f58e35-5cce-4ff2-9afc-b2d9d0f819cf
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 82532fc2864bcb4c19b0cf122e60fd9a64b2dbf9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62952921"
---
# <a name="invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Visual Studio Debugger for Windows Workflow Foundation 호출(레거시)
이 항목에서는 레거시 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 [!INCLUDE[wf](../includes/wf-md.md)] 디버거를 사용하여 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 애플리케이션을 디버깅하는 방법에 대해 설명합니다. 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

 일반적으로 레거시 워크플로를 디버깅하는 과정은 다른 Visual Studio 프로그래밍 언어로 작성된 프로그램을 디버깅하는 과정과 같습니다. 다음 방법으로 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for Windows Workflow Foundation을 시작할 수 있습니다.

- 선택 **프로세스에 연결** 에 **디버그** 메뉴를 사용 가능한 프로세스에서 실행 중인 워크플로 인스턴스를 선택 합니다.

- 키를 눌러 **F5** 워크플로 인스턴스의 실행을 시작 하거나 중단점이 적중 된 후 실행을 계속 합니다.

## <a name="stepping-through-code"></a>단계별 코드 실행
 디버거는 가장 일반적인 디버깅 절차 중 하나인, 한 번에 한 줄씩 코드를 실행하는 단계별 실행을 지원합니다. 단계별 코드 실행 명령에는 세 가지가 있습니다.

- **단계**: 사용 하 여 활동을 한 단계씩 실행할 수 **F11**합니다. 디버거는 정의된 임의의 처리기에서 한 단계씩 코드를 실행합니다. 정의된 처리기가 없으면 해당 활동을 프로시저 단위로 실행합니다. 다른 활동이 포함된 복합 활동의 경우 실행 중인 첫 번째 활동을 단계적으로 실행합니다. 디자이너에서 코드 처리기를 한 단계씩 실행에서 다음과 같은 작업에 대 한 지원 되지 않습니다. **IfElseActivity**하십시오 **WhileActivity**, **ConditionedActivityGroup**, 또는 **ReplicatorActivity**합니다. 이러한 활동과 연결된 처리기를 디버깅하려면 코드에 명시적인 중단점을 넣어야 합니다.

- **프로시저 나가기**: 사용 하 여 활동에서 나갈 수 있습니다 **Shift-F11**합니다. 활동에서 나가기를 수행하면 현재 활동 및 모든 형제 활동이 완료 시까지 실행됩니다. 그런 다음 디버거는 현재 활동의 부모에서 중단합니다. 코드 처리기에서 나갈 때 디버거는 처리기가 연결된 활동에서 중단합니다.

- **프로시저 단위 실행**: 사용 하는 작업 단위로 실행할 수 있습니다 **F10**합니다. 복합 활동을 프로시저 단위로 실행할 때 디버거는 복합 활동의 첫 번째 실행 가능 자식에서 중단합니다. 와 같은 비 복합을 단계별로 실행 하는 경우는 **CodeActivity** 다음 활동에서 활동와 연결 된 처리기 및 나누기를 실행 하는 작업을 디버거. 실행되는 활동이 복합 활동 중 마지막 자식 활동인 경우, 실행 후에 디버거는 부모 활동에서 중단합니다.

## <a name="attaching-to-a-process"></a>프로세스에 연결
 프로세스에 연결 하 여 워크플로 디버깅 하려면에서 사용 가능한 프로세스를 선택 합니다 **사용 가능한 프로세스** 목록 상자에서를 **프로세스에 연결** 대화 상자. 경우 **자동: 워크플로 코드** 에 표시 되지 않습니다 합니다 **연결할** 텍스트 상자, 클릭 **선택**합니다. 에 **코드 형식 선택** 대화 상자, 클릭 **다음 코드 형식 디버깅** 선택한 **워크플로**합니다. 누른 **확인** 클릭 **연결**합니다.

## <a name="debugging-with-f5"></a>F5 키를 사용한 디버깅
 워크플로 디버깅 하려면 Visual Studio 솔루션 시작 프로젝트로 워크플로 DLL 프로젝트를 설정 해야 합니다는 워크플로 호스트 응용 프로그램과 워크플로 DLL에에서 있는 경우 다른 Visual Studio 프로젝트 예를 들어, 워크플로 활동 라이브러리를 사용 하는 경우 사용 하 여 **F5**합니다. 호스트 응용 프로그램과 워크플로 DLL 프로젝트의 경로 설정 해야 **시작 외부 프로그램** 속성입니다.

 솔루션 탐색기에서 시작 프로젝트를 설정 하려면 프로젝트 이름을 마우스 오른쪽 단추로 클릭 하 고 선택 **시작 프로젝트로 설정**합니다. 호스트에 경로 설정 하는 **시작 외부 프로그램** 속성을 워크플로 프로젝트를 두 번 클릭 **속성** 선택 하 고 솔루션 탐색기에서 노드를 **디버그** 탭입니다. 아래 **시작 작업**를 선택 **시작 외부 프로그램** 디버깅 하려면 워크플로 호스트 하는.exe 파일의 경로 입력 합니다.

 호스트 애플리케이션이 시작 프로젝트로 설정되는 경우 Visual Studio 디버거만 디버깅을 위해 호출됩니다. [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for Windows Workflow Foundation은 호출되지 않습니다. Visual Studio 디버거가 사용되는 경우 C# 또는 Visual Basic 코드 중단점만 적중됩니다. 워크플로 디자이너에 설정된 중단점은 적중되지 않습니다. 예를 들어 디자이너에서 <xref:System.Workflow.Activities.ParallelActivity> 활동에 대해 설정한 중단점은 [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] Debugger for Windows Workflow Foundation이 사용되는 경우에 적중되지만 Visual Studio 디버거 사용 시에는 적중되지 않습니다.

## <a name="see-also"></a>참고 항목
 [방법: (레거시) 워크플로에 중단점 설정](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [레거시 워크플로 디버깅](../workflow-designer/debugging-legacy-workflows.md)