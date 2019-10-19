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
ms.openlocfilehash: bc4ef840310c27ccbadce2ed4f632514b555ef98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575649"
---
# <a name="scriptthreadstate-enumeration"></a>SCRIPTTHREADSTATE 열거형
스크립팅 엔진의 스레드 상태를 지정 합니다. 이 열거형은 [IActiveScript:: GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md) 메서드에서 사용 됩니다.  
  
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
|SCRIPTTHREADSTATE_NOTINSCRIPT|지정 된 스레드가 현재 스크립팅된 이벤트를 처리 하 고 있거나 스크립트 텍스트를 즉시 실행 하거나 스크립트 매크로를 실행 하 고 있지 않습니다.|  
|SCRIPTTHREADSTATE_RUNNING|지정 된 스레드가 스크립팅된 이벤트를 처리 하거나, 즉시 실행 되는 스크립트 텍스트를 처리 하거나, 스크립트 매크로를 실행 하 고 있습니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 상수, 열거형 및 오류 코드](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)