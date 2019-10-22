---
title: 'IActiveScriptWinRTErrorDebug:: GetCapabilitySid | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetCapabilitySid
ms.assetid: 469463d2-5e73-4c53-9ffd-d0ca7460aa5c
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93bf824dd4d290ca536cb609e24b5d14400a3e3b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577927"
---
# <a name="iactivescriptwinrterrordebuggetcapabilitysid"></a>IActiveScriptWinRTErrorDebug::GetCapabilitySid
사용 가능한 경우 Windows 런타임 오류에 대 한 기능 SID를 반환 합니다.  
  
> [!IMPORTANT]
> [IActiveScriptWinRTErrorDebug 인터페이스](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetCapabilitySid([out] BSTR * capabilitySid);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `capabilitySid`  
 오류의 기능 SID입니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptWinRTErrorDebug 인터페이스](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)