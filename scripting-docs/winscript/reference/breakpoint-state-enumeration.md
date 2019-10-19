---
title: BREAKPOINT_STATE 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- BREAKPOINT_STATE
apilocation:
- scrobj.dll
helpviewer_keywords:
- BREAKPOINT_STATE enumeration
ms.assetid: 7adc9341-129a-4948-9669-0906d545fd5c
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8c56a8b135a0aa9a4f8ddf91e146d4d64367bb2b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572640"
---
# <a name="breakpoint_state-enumeration"></a>BREAKPOINT_STATE 열거형
중단점의 상태를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef enum tagBREAKPOINT_STATE {  
   BREAKPOINT_DELETED = 0,  
   BREAKPOINT_DISABLED = 1,  
   BREAKPOINT_ENABLED = 2  
} BREAKPOINT_STATE;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|설명|  
|------------|-----------------|  
|BREAKPOINT_DELETED|중단점은 더 이상 존재 하지 않지만 여전히 참조가 있습니다.|  
|BREAKPOINT_DISABLED|중단점이 있지만 사용할 수 없습니다.|  
|BREAKPOINT_ENABLED|중단점이 있고 사용 하도록 설정 되어 있습니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)