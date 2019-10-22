---
title: 사이의 이유 열거 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKREASON
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKREASON enumeration
ms.assetid: bde07ede-2f9b-4fa2-affc-f9405683f5f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f656bdf4e3bc85a014ff8d3011708799aa44bcd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572624"
---
# <a name="breakreason-enumeration"></a>BREAKREASON 열거형
중단된 원인을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef enum tagBREAKREASON {  
   BREAKREASON_STEP,  
   BREAKREASON_BREAKPOINT,  
   BREAKREASON_DEBUGGER_BLOCK,  
   BREAKREASON_HOST_INITIATED,  
   BREAKREASON_LANGUAGE_INITIATED,  
   BREAKREASON_DEBUGGER_HALT,  
   BREAKREASON_ERROR,  
   BREAKREASON_JIT  
} BREAKREASON;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|BREAKREASON_STEP|언어 엔진이 단계별 모드입니다.|  
|BREAKREASON_BREAKPOINT|언어 엔진에서 명시적 중단점이 발생 했습니다.|  
|BREAKREASON_DEBUGGER_BLOCK|언어 엔진에서 다른 스레드에 디버거 블록이 발생 했습니다.|  
|BREAKREASON_HOST_INITIATED|호스트에서 중단을 요청 했습니다.|  
|BREAKREASON_LANGUAGE_INITIATED|언어 엔진이 중단을 요청 했습니다.|  
|BREAKREASON_DEBUGGER_HALT|디버거 IDE에서 중단을 요청 했습니다.|  
|BREAKREASON_ERROR|실행 오류가 발생 하 여 중단 되었습니다.|  
|BREAKREASON_JIT|JIT 디버깅 시작으로 인 한 것입니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)