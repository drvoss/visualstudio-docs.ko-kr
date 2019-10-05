---
title: '방법: 워크플로 디버거 호출 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 34c592af-f4f6-4d02-99f6-63a94698e48b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a3d5033bc9953aa00efb950eabce5e7346952f9d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444159"
---
# <a name="how-to-invoke-the-workflow-debugger"></a>방법: 워크플로 디버거 호출
일반적으로 워크플로 디버깅은 다른 Visual Studio 프로그래밍 언어로 작성된 프로그램의 디버깅과 동일합니다. 다음과 같은 방법으로 워크플로 디버거를 시작할 수 있습니다.  
  
- 선택 **프로세스에 연결** 에 **디버그** 메뉴 워크플로 인스턴스에 대 한 실행 중인 호스트 프로세스를 선택 합니다. 이 절차는 관리 코드의 호스트 프로세스에 연결하는 절차와 동일합니다.  
  
- 키를 눌러 **F5** 워크플로 인스턴스의 실행을 시작 하거나 중단점이 적중 된 후 실행을 계속 합니다.  
  
- 원격 디버깅을 사용합니다. 원격 디버깅 사용에 대 한 자세한 내용은 [방법: 원격 디버깅 사용](http://go.microsoft.com/fwlink/?LinkId=196257)합니다.  
  
    > [!NOTE]
    > 워크플로 응용 프로그램은 x86을 대상으로 하는 경우 아키텍처 원격 디버깅을 작동 하는 고 64 비트 운영 체제를 실행 하는 컴퓨터에서 호스트 될 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] 워크플로 응용 프로그램에 변경 된 원격 컴퓨터 또는 대상에 설치 되어 **임의 CPU**합니다.  
  
### <a name="stepping-through-code"></a>단계별 코드 실행  
  
- **단계**: 사용 하 여 활동을 한 단계씩 실행할 수 **F11**합니다. 디버거는 정의된 임의의 처리기에서 한 단계씩 코드를 실행합니다. 정의된 처리기가 없으면 해당 활동을 프로시저 단위로 실행합니다. 다른 활동이 포함된 복합 활동의 경우 실행 중인 첫 번째 활동을 단계적으로 실행합니다.  
  
- **프로시저 나가기:** 사용 하 여 활동에서 나갈 수 있습니다 **Shift-F11**합니다. 활동에서 나가기를 수행하면 현재 활동 및 모든 형제 활동이 완료 시까지 실행됩니다. 그런 다음 디버거는 현재 활동의 부모에서 중단합니다. 코드 처리기에서 나갈 때 디버거는 처리기가 연결된 활동에서 중단합니다.  
  
- **프로시저 단위 실행**: 사용 하는 작업 단위로 실행할 수 있습니다 **F10**합니다. 복합 활동을 프로시저 단위로 실행할 때 디버거는 복합 활동의 첫 번째 실행 가능 자식에서 중단합니다. <xref:System.Activities.Statements.Assign> 활동과 같은 비복합 활동을 프로시저 단위로 실행할 경우 디버거는 해당 활동 및 그와 연결된 처리기를 실행하고 다음 활동에서 중단합니다. 실행할 활동이 복합 활동 중 마지막 자식 활동인 경우, 디버거는 활동 실행 후 부모 활동에서 중단합니다.  
  
### <a name="debugging-with-f5"></a>F5 키를 사용한 디버깅  
  
- 워크플로 콘솔 응용 프로그램 프로젝트를 빌드하는 경우 누르기만 **F5** 응용 프로그램 및 워크플로를 디버깅을 시작 합니다. 활동 라이브러리를 자체적으로 빌드하려는 경우 시작 프로젝트인 실행 가능 호스트 애플리케이션이 있어야 합니다. 시작 프로젝트를 설정 하려면 **솔루션 탐색기**, 호스트의 프로젝트 이름을 마우스 오른쪽 단추로 **시작 프로젝트로 설정**합니다.  
  
## <a name="see-also"></a>참고 항목  
 [방법: 워크플로에 중단점 설정](../workflow-designer/how-to-set-breakpoints-in-workflows.md)   
 [워크플로 디자이너로 워크플로 디버깅](../workflow-designer/debugging-workflows-with-the-workflow-designer.md)