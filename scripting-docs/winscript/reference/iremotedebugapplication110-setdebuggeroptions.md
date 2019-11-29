---
title: 'IRemoteDebugApplication110:: SetDebuggerOptions | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::SetDebuggerOptions
ms.assetid: 58e9fd18-3e0d-47fa-8893-f316146bde84
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7168a4ef8ec70368c0ff691ba1f721275f9d65d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577420"
---
# <a name="iremotedebugapplication110setdebuggeroptions"></a>IRemoteDebugApplication110::SetDebuggerOptions
디버거 옵션을 업데이트 하기 위해 호출 됩니다. 이 메서드는 [Iremotedebugapplication:: ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)후에 호출 해야 합니다. [Iremotedebugapplication::D isconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md) 메서드는 기본 옵션으로 자동으로 다시 설정 됩니다. 옵션의 기본값은 0 (SDO_NONE)입니다.  
  
> [!IMPORTANT]
> [Iremotedebugapplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT SetDebuggerOptions(        [in] enum SCRIPT_DEBUGGER_OPTIONS mask,        [in] enum SCRIPT_DEBUGGER_OPTIONS value    );  
```  
  
#### <a name="parameters"></a>매개 변수  
 `mask`  
 [SCRIPT_DEBUGGER_OPTIONS 열거형](../../winscript/reference/script-debugger-options-enumeration.md) 마스크입니다.  
  
 `value`  
 [SCRIPT_DEBUGGER_OPTIONS 열거형](../../winscript/reference/script-debugger-options-enumeration.md) 값입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Iremotedebugapplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 인터페이스](../../winscript/reference/iremotedebugapplication110-interface.md)