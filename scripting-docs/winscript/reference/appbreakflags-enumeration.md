---
title: APPBREAKFLAGS 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- APPBREAKFLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- APPBREAKFLAGS constants
ms.assetid: ea8ed80f-2ddb-4800-bb3b-52b76ba6c7a0
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de6efbc20843fcaa73965334c18cf0e5c2a0abab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572666"
---
# <a name="appbreakflags-enumeration"></a>APPBREAKFLAGS 열거형
현재 애플리케이션 및 스레드에 대한 디버그 상태를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
enum enum_APPBREAKFLAGS{APPBREAKFLAG_DEBUGGER_BLOCK= 0x00000001,APPBREAKFLAG_DEBUGGER_HALT= 0x00000002,APPBREAKFLAG_STEP= 0x00010000,APPBREAKFLAG_NESTED= 0x00020000,APPBREAKFLAG_STEPTYPE_SOURCE= 0x00000000,APPBREAKFLAG_STEPTYPE_BYTECODE= 0x00100000,APPBREAKFLAG_STEPTYPE_MACHINE= 0x00200000,APPBREAKFLAG_STEPTYPE_MASK= 0x00F00000,APPBREAKFLAG_IN_BREAKPOINT= 0x80000000};  
```  
  
## <a name="members"></a>멤버  
  
|멤버|값|설명|  
|------------|-----------|-----------------|  
|APPBREAKFLAG_DEBUGGER_BLOCK|0x00000001|언어 엔진은 BREAKREASON_DEBUGGER_BLOCK를 사용 하는 모든 스레드에서 즉시 중단 되어야 합니다.|  
|APPBREAKFLAG_DEBUGGER_HALT|0x00000002|언어 엔진은 BREAKREASON_DEBUGGER_HALT를 사용 하 여 즉시 중단 되어야 합니다.|  
|APPBREAKFLAG_STEP|0x00010000|언어 엔진은 BREAKREASON_STEP를 사용 하 여 단계별 스레드에서 즉시 중단 되어야 합니다.|  
|APPBREAKFLAG_NESTED|0x00020000|응용 프로그램이 중단점에서 중첩 된 실행에 있습니다.|  
|APPBREAKFLAG_STEPTYPE_SOURCE|0x00000000|디버거가 소스 수준에서 단계별로 실행 됩니다.|  
|APPBREAKFLAG_STEPTYPE_BYTECODE|0x00100000|디버거는 바이트 코드 수준에서 단계별로 실행 됩니다.|  
|APPBREAKFLAG_STEPTYPE_MACHINE|0x00200000|디버거가 컴퓨터 수준에서 단계별로 실행 됩니다.|  
|APPBREAKFLAG_STEPTYPE_MASK|0x00F00000|단계 유형을 구분 하는 마스크입니다.|  
|APPBREAKFLAG_IN_BREAKPOINT|0x80000000|중단점이 진행 중입니다.|  
  
## <a name="remarks"></a>주의  
 일부 플래그는 언어 엔진이 다음 기회에서 중단 되어야 함을 지정 하는 반면 다른 플래그는 디버거의 단계별 실행 모드를 지정 합니다.  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)    
 [BREAKREASON 열거형](../../winscript/reference/breakreason-enumeration.md)