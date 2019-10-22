---
title: SCRIPT_DEBUGGER_OPTIONS 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SCRIPT_DEBUGGER_OPTIONS Enumeration
ms.assetid: aef41ec0-6f65-48e8-a69e-44b4e4fb929f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c69d419732786442cda275bf85c74ab2b9d3e870
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574556"
---
# <a name="script_debugger_options-enumeration"></a>SCRIPT_DEBUGGER_OPTIONS 열거형
연결 된 디버거에 적용 되는 옵션 및/또는 기능 집합을 나타냅니다. [IDebugApplicationNode100:: GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) 및 [IDebugApplicationNode100:: SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md) 에 사용 됩니다.  
  
> [!IMPORTANT]
> 이러한 상수는 PDM v 10.0 이상에서 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>멤버  
  
|멤버|값|설명|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|옵션은 설정 되지 않습니다.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|예외가 throw 될 때 스크립트 런타임이 BREAKREASON_ERROR 이벤트를 발생 시 키도 록 지정 합니다. 이 옵션은 디버거에서 설정 하거나 `Debug.enableFirstChanceExceptions(<true&#124;false>)`를 통해 사용자 코드를 사용 하 여 설정할 수 있습니다.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|연결 된 디버거가 웹 작업자를 지원함을 나타냅니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)