---
title: SCRIPTTHREADSTATE 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- SCRIPTTHREADSTATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- SCRIPTTHREADSTATE enum
ms.assetid: 975ec66b-c095-40ac-8ba9-631adb97b589
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 906a309b25a1fe606fb37f8cbab70040e5a4c46f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840189"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE 열거형
스크립팅 엔진의 스레드 상태를 지정합니다. 이 열거형은에서 사용 된 [IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) 메서드.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef enum tagSCRIPTTHREADSTATE {  
    SCRIPTTHREADSTATE_NOTINSCRIPT  = 0,  
    SCRIPTTHREADSTATE_RUNNING      = 1  
} SCRIPTTHREADSTATE;  
```  
  
## <a name="enumeration-values"></a>열거형 값  
  
|||  
|-|-|  
|SCRIPTTHREADSTATE_NOTINSCRIPT|지정 된 스레드에 스크립팅된 이벤트를 즉시 실행 하는 처리 스크립트 텍스트를 처리 또는 스크립트 매크로 실행 합니다. 현재는 아닙니다.|  
|SCRIPTTHREADSTATE_RUNNING|지정 된 스레드에 스크립트를 사용한 이벤트를 즉시 실행 하는 처리 스크립트 텍스트를 처리 또는 스크립트 매크로 실행 적극적으로.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 상수, 열거형 및 오류 코드](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)