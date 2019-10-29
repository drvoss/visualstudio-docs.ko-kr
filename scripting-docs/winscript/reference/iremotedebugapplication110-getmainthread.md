---
title: 'IRemoteDebugApplication110:: GetMainThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication110::GetMainThread
ms.assetid: 9982acc9-3d35-4dcf-8ca9-662469de4072
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8e4ae024429702f3268a01c1e2e1fb4b40294d8
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985282"
---
# <a name="iremotedebugapplication110getmainthread"></a>IRemoteDebugApplication110::GetMainThread
[SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite)를 호출 하는 호스트에 대 한 주 스레드를 반환 합니다. 그렇지 않으면 E_FAIL을 반환 합니다.  
  
> [!IMPORTANT]
> [Iremotedebugapplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetMainThread([out] IRemoteDebugApplicationThread **ppThread);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppThread`  
 제한이 기본 [Iremotedebugapplicationthread 인터페이스](../../winscript/reference/iremotedebugapplicationthread-interface.md)입니다.  
  
## <a name="see-also"></a>참조  
 [Iremotedebugapplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md)    
 [IRemoteDebugApplication110 인터페이스](../../winscript/reference/iremotedebugapplication110-interface.md)