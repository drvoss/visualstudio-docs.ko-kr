---
title: 메시지 열거자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- message enumerator
- source control plug-ins, message enumeration
ms.assetid: 4a4faa0d-d352-40ea-a21d-c09ea286a8e1
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6bd42c825cd45068e13178856e524268b426ec53
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194333"
---
# <a name="message-enumerator"></a>메시지 열거자
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음 플래그에 사용 되는 `TEXTOUTPROC` 함수를 호출할 때 IDE에서 제공 하는 콜백 함수를 [SccOpenProject](../extensibility/sccopenproject-function.md) (참조 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) 콜백에 대 한 자세한 내용은 함수 사용)입니다.  
  
 IDE는 프로세스를 취소 하 라는 메시지가 표시 됩니다, 경우 취소 메시지 중 하나가 발생할 수 있습니다. 이 경우 원본 제어 플러그 인 사용 `SCC_MSG_STARTCANCEL` 표시할 IDE를 요청 하는 **취소** 단추입니다. 그러면 모든 집합이 일반 메시지를 보낼 수 있습니다. 이러한 반환 중 하나가 되 면 `SCC_MSG_RTN_CANCEL`, 플러그 인 작업을 종료 하 고 반환 합니다. 플러그 인을 들 여도 폴링합니다 `SCC_MSG_DOCANCEL` 주기적으로 결정할 경우 사용자가 작업을 취소 합니다. 모든 작업을 마쳤으면 보내거나 사용자가 취소 하는 경우 플러그 인 경우 `SCC_MSG_STOPCANCEL`합니다. `SCC_MSG_INFO`, SCC_MSG_WARNING, SCC_MSG_ERROR 형식 스크롤 메시지 목록에 표시 되는 메시지에 사용 되 고 있습니다. `SCC_MSG_STATUS` 상태 표시줄 또는 임시 표시 영역에서 텍스트 표시 해야 나타내는 특수 형식이입니다. 목록에는 영구적으로 유지 되지 않습니다.  
  
## <a name="syntax"></a>구문  
  
```  
enum {   
   SCC_MSG_RTN_CANCEL = -1,   
   SCC_MSG_RTN_OK = 0,   
   SCC_MSG_INFO = 1   
   SCC_MSG_WARNING,   
   SCC_MSG_ERROR,   
   SCC_MSG_STATUS,   
   SCC_MSG_DOCANCEL,   
   SCC_MSG_STARTCANCEL,   
   SCC_MSG_STOPCANCEL   
};  
```  
  
## <a name="members"></a>멤버  
 SCC_MSG_RTN_CANCEL  
 취소를 나타내기 위해 콜백에서 반환 합니다.  
  
 SCC_MSG_RTN_OK  
 계속 하려면 콜백에서 반환 합니다.  
  
 SCC_MSG_INFO  
 메시지는 알림입니다.  
  
 SCC_MSG_WARNING  
 메시지는 경고입니다.  
  
 SCC_MSG_ERROR  
 메시지 오류입니다.  
  
 SCC_MSG_STATUS  
 메시지 상태 표시줄에 대 한 것입니다.  
  
 SCC_MSG_DOCANCEL  
 텍스트가 없습니다. IDE 반환 `SCC_MSG_RTN_OK` 또는 `SCC_MSG_RTN_CANCEL`합니다.  
  
 SCC_MSG_STARTCANCEL  
 취소 루프를 시작합니다.  
  
 SCC_MSG_STOPCANCEL  
 취소 루프를 중지합니다.  
  
## <a name="see-also"></a>참고 항목  
 [원본 제어 플러그 인](../extensibility/source-control-plug-ins.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)
