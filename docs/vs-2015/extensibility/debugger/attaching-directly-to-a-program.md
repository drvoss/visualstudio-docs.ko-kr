---
title: 프로그램에 직접 연결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab49163fc1474b541df3bc1b54d336574761baa3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147992"
---
# <a name="attaching-directly-to-a-program"></a>프로그램에 직접 연결
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

일반적으로 이미 실행 중인 프로세스에서 프로그램을 디버그 하려는 사용자는이 프로세스를 수행 합니다.  
  
1. IDE에서 선택 합니다 **프로세스 디버그** 에서 명령을 합니다 **도구** 메뉴.  
  
    **프로세스** 대화 상자가 표시됩니다.  
  
2. 프로세스를 선택 하 고 클릭 합니다 **연결** 단추입니다.  
  
    합니다 **프로세스에 연결** 대화 상자가 나타나면 컴퓨터에 설치 된 모든 디버그 엔진 (DEs)를 나열 합니다.  
  
3. 사용 하 고 선택한 프로세스를 디버그 하 고 클릭 DEs 지정할 **확인**합니다.  
  
   디버그 패키지 디버그 세션을 시작 하 고 해당 DEs 목록을 전달 합니다. 디버그 세션 선택한 프로세스에 콜백 함수를 함께이 목록에 전달 하 고 실행 중인 프로그램을 열거 하는 프로세스를 요청 합니다.  
  
   프로그래밍 방식으로 사용자 요청에 응답을 디버그 패키지 인스턴스화합니다 세션 디버그 관리자 SDM ()를 선택한 DEs 목록을 전달 합니다. 디버그 패키지 목록 함께 SDM을 전달 된 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) 인터페이스입니다. 디버그 패키지가 DEs 목록을 선택한 프로세스를 호출 하 여 전달 [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)합니다. SDM 호출 [IDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) 프로세스에서 실행 중인 프로그램을 열거 하는 포트입니다.  
  
   이 시점에서 각 디버그 엔진에 설명 된 대로 정확 하 게 프로그램에 연결 된 [연결 후는 시작](../../extensibility/debugger/attaching-after-a-launch.md), 두 가지 예외를 사용 하 여 합니다.  
  
   효율성을 높이기 위해 DEs SDM을 사용 하 여 주소 공간을 공유 하도록 구현 된 각 장치를 연결할 프로그램 집합을 갖도록 그룹화 됩니다. 이 예에서 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) 호출 [IDebugEngine2::Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) 연결할 프로그램 배열을 전달 합니다.  
  
   두 번째 예외는 이미 실행 중인 프로그램에 연결 하는 독일에서 보낸 시작 이벤트 일반적으로 포함 하지 항목 지점 이벤트입니다.  
  
## <a name="see-also"></a>참고 항목  
 [시작 후 시작 이벤트 보내기](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [디버깅 작업](../../extensibility/debugger/debugging-tasks.md)
