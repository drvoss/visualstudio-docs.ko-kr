---
title: BREAKREASON 열거형 | Microsoft Docs
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
ms.openlocfilehash: 939d9f36c9838f02e58bc433d1a7bb9bef43c28d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955410"
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
|BREAKREASON_STEP|언어 엔진 단계별 실행 모드입니다.|  
|BREAKREASON_BREAKPOINT|언어 엔진에 명시적 중단점을 발생 합니다.|  
|BREAKREASON_DEBUGGER_BLOCK|언어 엔진 디버거 블록을 다른 스레드에서 발생 합니다.|  
|BREAKREASON_HOST_INITIATED|호스트 요청을 중단 합니다.|  
|BREAKREASON_LANGUAGE_INITIATED|언어 엔진 나누기를 요청 합니다.|  
|BREAKREASON_DEBUGGER_HALT|디버거 IDE 나누기를 요청 합니다.|  
|BREAKREASON_ERROR|실행 오류가 발생 하 여 중단 합니다.|  
|BREAKREASON_JIT|JIT 디버깅이 시작에 의해 발생합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)