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
ms.openlocfilehash: 404d3939e0a328beb5e2413d25885fddf8478ead
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443641"
---
# <a name="scriptdebuggeroptions-enumeration"></a>SCRIPT_DEBUGGER_OPTIONS 열거형
옵션 및/또는 연결 된 디버거에 적용 하는 기능 집합을 나타냅니다. 레지스트리에 [IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md) 고 [IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)  
  
> [!IMPORTANT]
> 이러한 상수는 PDM v10.0에서 큰 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef SCRIPT_DEBUGGER_OPTIONS  
```  
  
## <a name="members"></a>멤버  
  
|멤버|값|설명|  
|------------|-----------|-----------------|  
|SDO_NONE|0x00000000|옵션이 설정 되지 않았습니다.|  
|SDO_ENABLE_FIRST_CHANCE_EXCEPTIONS|0x00000001|스크립트 런타임 예외가 throw 되 면 BREAKREASON_ERROR 이벤트를 발생시킬지를 나타냅니다. 이 옵션 디버거에 의해 설정 되었거나 사용자 코드를 통해 설정한 `Debug.enableFirstChanceExceptions(<true&#124;false>)`합니다.|  
|SDO_ENABLE_WEB_WORKER_SUPPORT|0x00000002|연결된 된 디버거에 웹 작업자를 지원함을 나타냅니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)