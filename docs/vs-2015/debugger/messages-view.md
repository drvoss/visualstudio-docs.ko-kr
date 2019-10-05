---
title: 메시지 뷰 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.externaltools.spyplus.messagesview
helpviewer_keywords:
- Messages view
ms.assetid: 14c2a786-c23a-4b2d-acad-8c32a856c70d
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3765b9804224549c98b57cd1b0a44f0330d278b5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157476"
---
# <a name="messages-view"></a>메시지 뷰
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

각 창에는 관련된 메시지 스트림이 있습니다. 메시지 보기 창에는이 메시지 스트림을 표시합니다. 창 핸들, 메시지 코드 및 메시지가 표시 됩니다. 스레드 또는 프로세스에 대 한 메시지 보기를 만들 수 있습니다. 이 옵션을 사용 하면 특정 프로세스 또는 스레드 창 초기화 메시지를 캡처하는 데 특히 유용는 소유 하는 모든 창에 전송 된 메시지를 볼 수 있습니다.  
  
 아래는 일반적인 메시지 보기 창에 나타납니다. 첫 번째 열에는 창 핸들을 포함 하 고 두 번째 열에는 메시지 코드가 포함 되어 있습니다. (에서 설명한 [메시지 코드](../debugger/message-codes.md)). 디코딩된 메시지 매개 변수 및 반환 값은 오른쪽에 있습니다.  
  
 ![Spy&#43; &#43; 메시지 뷰](../debugger/media/spy-messagesview.png "Spy + + _MessagesView")  
Spy++ 메시지 뷰  
  
## <a name="procedures"></a>절차  
  
#### <a name="to-open-a-messages-view-for-a-window-process-or-thread"></a>창, 프로세스 또는 스레드 메시지 보기를 열려면  
  
1. 포커스를 이동 하는 [Windows 뷰](../debugger/windows-view.md), [프로세스 뷰에](../debugger/processes-view.md), 또는 [스레드 뷰](../debugger/threads-view.md) 창입니다.  
  
2. 항목을 검사 하려는 해당 메시지에 대 한 노드를 찾아 선택 합니다.  
  
3. **Spy** 메뉴 선택 **로그 메시지**합니다.  
  
     합니다 [메시지 옵션 대화 상자](../debugger/message-options-dialog-box.md) 열립니다.  
  
4. 표시할 메시지에 대 한 옵션을 선택 합니다.  
  
5. 키를 눌러 **확인** 메시지 로깅을 시작 합니다.  
  
     및 메시지 보기 창이 열리고 **메시지** 메뉴가 Spy + + 도구 모음에 추가 됩니다. 선택한 옵션에 따라 활성 메시지 보기 창으로 스트리밍되 기 시작 합니다.  
  
6. 충분 한 메시지에 있는 경우 선택할 **로깅 중지** 에서 합니다 **메시지** 메뉴.  
  
## <a name="in-this-section"></a>섹션 내용  
 [메시지 뷰 제어](../debugger/how-to-control-messages-view.md)  
 메시지 보기를 관리 하는 방법에 설명 합니다.  
  
 [메시지 뷰에서 메시지 검색](../debugger/how-to-search-for-a-message-in-messages-view.md)  
 메시지 보기에서 특정 메시지를 찾는 방법에 설명 합니다.  
  
 [시작 및 메시지 로그 표시를 중지 합니다.](../debugger/how-to-start-and-stop-the-message-log-display.md)  
 메시지 로깅을 시작 및 중지 하는 방법에 설명 합니다.  
  
 [메시지 코드](../debugger/message-codes.md)  
 메시지 보기에 나열 된 메시지에 대 한 코드를 정의 합니다.  
  
 [메시지 속성 표시](../debugger/how-to-display-message-properties.md)  
 메시지에 대 한 자세한 정보를 표시 하는 방법.  
  
## <a name="related-sections"></a>관련 단원  
 [Spy++ 뷰](../debugger/spy-increment-views.md)  
 Windows, 메시지, 프로세스 및 스레드 Spy + + 트리 보기에 설명합니다.  
  
 [Spy++ 사용](../debugger/using-spy-increment.md)  
 Spy + + 도구를 소개 하 고 사용할 수 있는 방법을 설명 합니다.  
  
 [메시지 옵션 대화 상자](../debugger/message-options-dialog-box.md)  
 현재 메시지 보기에 표시 되는 메시지를 선택 하는 데 사용 합니다.  
  
 [메시지 검색 대화 상자](../debugger/message-search-dialog-box.md)  
 메시지 보기에서 특정 메시지에 대 한 노드를 찾는 데 사용 합니다.  
  
 [메시지 속성 대화 상자](../debugger/message-properties-dialog-box.md)  
 메시지 보기에서 선택한 메시지의 속성을 표시 하는 데 사용 합니다.  
  
 [Spy++ 참조](../debugger/spy-increment-reference.md)  
 각 Spy + + 메뉴 및 대화 상자를 설명 하는 섹션을 포함 합니다.
