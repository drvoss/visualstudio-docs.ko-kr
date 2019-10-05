---
title: Workflow Designer로 워크플로 디버깅
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Workflow Designer [WFD], debugging workflows
- Workflow Designer [WFD], debugging workflows
ms.assetid: d71308cf-d464-4536-8711-0d0a8eadb255
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1270e57ae6c9235311569c04ebb982157ea3b608
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62949749"
---
# <a name="debug-workflows-with-the-workflow-designer"></a>워크플로 디자이너로 워크플로 디버깅

합니다 **워크플로 디자이너** 워크플로 및 사용자 지정 활동을 디버깅 하는 기능을 제공 합니다. 프로세스와 동작은 기본 Visual Studio 디버거는 비슷합니다.

## <a name="invoke-the-workflow-debugger"></a>워크플로 디버거 호출

일반적으로 워크플로 디버깅은 다른 Visual Studio 프로그래밍 언어로 작성된 프로그램의 디버깅과 동일합니다. 다음과 같은 방법으로 워크플로 디버거를 시작할 수 있습니다.

- 선택 **프로세스에 연결** 에 **디버그** 메뉴 워크플로 인스턴스에 대 한 실행 중인 호스트 프로세스를 선택 합니다. 이 절차는 관리 코드의 호스트 프로세스에 연결하는 절차와 동일합니다.

- 키를 눌러 **F5** 워크플로 인스턴스의 실행을 시작 하거나 중단점이 적중 된 후 실행을 계속 합니다.

- 원격 디버깅을 사용합니다. 원격 디버깅 사용에 대 한 자세한 내용은 [방법: 원격 디버깅 사용](/previous-versions/visualstudio/visual-studio-2010/febz73k0(v=vs.100))합니다.

   > [!NOTE]
   > 워크플로 응용 프로그램은 x86을 대상으로 하는 경우 아키텍처 원격 디버깅이 작동 하지 않습니다 원격 컴퓨터의 Visual Studio가 설치 되어 아니면 워크플로 응용 프로그램에 대 한 대상 로변경되고64비트운영체제를실행하는컴퓨터에서호스트될 **모든 CPU**합니다.

## <a name="step-through-code"></a>단계별 코드 실행

- **단계**: 키를 눌러 작업으로 단계 **F11**합니다. 디버거는 정의된 임의의 처리기에서 한 단계씩 코드를 실행합니다. 정의된 처리기가 없으면 해당 활동을 프로시저 단위로 실행합니다. 다른 활동이 포함된 복합 활동의 경우 실행 중인 첫 번째 활동을 단계적으로 실행합니다.

- **프로시저 나가기:** 키를 눌러 작업을 벗어난 단계 **Shift**+**F11**합니다. 활동에서 나가기를 수행하면 현재 활동 및 모든 형제 활동이 완료 시까지 실행됩니다. 그런 다음 디버거는 현재 활동의 부모에서 중단합니다. 코드 처리기에서 나갈 때 디버거는 처리기가 연결된 활동에서 중단합니다.

- **프로시저 단위 실행**: 키를 눌러 작업 건너뛰기 **F10**합니다. 복합 활동을 프로시저 단위로 실행할 때 디버거는 복합 활동의 첫 번째 실행 가능 자식에서 중단합니다. <xref:System.Activities.Statements.Assign> 활동과 같은 비복합 활동을 프로시저 단위로 실행할 경우 디버거는 해당 활동 및 그와 연결된 처리기를 실행하고 다음 활동에서 중단합니다. 실행할 활동이 복합 활동 중 마지막 자식 활동인 경우, 디버거는 활동 실행 후 부모 활동에서 중단합니다.

## <a name="debug-with-f5"></a>F5 키를 사용 하 여 디버그

워크플로 콘솔 응용 프로그램을 빌드하는 경우 누르기만 **F5** 응용 프로그램 및 워크플로를 디버깅을 시작 합니다. 을 사용 하는 자체에서 활동 라이브러리를 작성 하는 경우 시작 프로젝트로 실행 호스트 응용 프로그램을 지정 해야 합니다. 시작 프로젝트를 설정 하려면 **솔루션 탐색기**, 호스트의 프로젝트 이름을 마우스 오른쪽 단추로 **시작 프로젝트로 설정**합니다.