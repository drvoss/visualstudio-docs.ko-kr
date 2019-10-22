---
title: BREAKRESUMEACTION 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKRESUMEACTION enumeration
ms.assetid: b39fcc82-7776-4caa-8155-b398de68df03
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2db56b66a544a31df3ac3a622568ecd29a33d12
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572612"
---
# <a name="breakresumeaction-enumeration"></a>BREAKRESUMEACTION 열거형
중단점에서 계속하는 방법을 설명합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef enum tagBREAKRESUME_ACTION {  
   BREAKRESUMEACTION_ABORT,  
   BREAKRESUMEACTION_CONTINUE,  
   BREAKRESUMEACTION_STEP_INTO,  
   BREAKRESUMEACTION_STEP_OVER,  
   BREAKRESUMEACTION_STEP_OUT,  
   BREAKRESUMEACTION_IGNORE,  
   BREAKRESUMEACTION_STEP_DOCUMENT,  
} BREAKRESUMEACTION;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|BREAKRESUMEACTION_ABORT|애플리케이션을 중단합니다.|  
|BREAKRESUMEACTION_CONTINUE|실행을 계속합니다.|  
|BREAKRESUMEACTION_STEP_INTO|프로시저를 한 단계씩 실행합니다.|  
|BREAKRESUMEACTION_STEP_OVER|절차를 건너뜁니다.|  
|BREAKRESUMEACTION_STEP_OUT|현재 프로시저에서 나갑니다.|  
|BREAKRESUMEACTION_IGNORE|상태를 유지하면서 실행을 계속합니다.|  
|BREAKRESUMEACTION_STEP_DOCUMENT|다음 문서로 한 단계씩 이동합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)