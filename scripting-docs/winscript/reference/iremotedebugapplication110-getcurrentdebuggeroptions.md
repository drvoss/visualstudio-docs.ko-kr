---
title: 'IRemoteDebugApplication110:: GetCurrentDebuggerOptions | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetCurrentDebuggerOptions
ms.assetid: a6e9cae1-e8f3-4d62-b133-52e9ca12ba7a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ae042a5d4d1c1ee350b328fdc5a9b7420d9928
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577437"
---
# <a name="iremotedebugapplication110getcurrentdebuggeroptions"></a>IRemoteDebugApplication110::GetCurrentDebuggerOptions
현재 사용할 수 있는 옵션 집합을 반환 합니다.  
  
> [!IMPORTANT]
> [Iremotedebugapplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetCurrentDebuggerOptions([out] enum SCRIPT_DEBUGGER_OPTIONS* pCurrentOptions);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pCurrentOptions`  
 제한이 현재 옵션입니다.  
  
## <a name="see-also"></a>참고 항목  
 [Iremotedebugapplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md)   
 [IRemoteDebugApplication110 인터페이스](../../winscript/reference/iremotedebugapplication110-interface.md)