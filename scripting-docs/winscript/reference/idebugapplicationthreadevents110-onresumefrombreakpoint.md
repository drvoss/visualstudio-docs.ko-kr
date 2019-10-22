---
title: 'IDebugApplicationThreadEvents110:: OnResumeFromBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnResumeFromBreakPoint
ms.assetid: 4c97b9a3-fced-487e-a81c-e3f8f2cb7927
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e710d259ae4985f6e37fc14ee70d0467578d2bd0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573358"
---
# <a name="idebugapplicationthreadevents110onresumefrombreakpoint"></a>IDebugApplicationThreadEvents110::OnResumeFromBreakPoint
스레드가 중단점에서 다시 시작 되 고 다시 한 번 활성화 됩니다.  
  
> [!IMPORTANT]
> [IDebugApplicationThreadEvents110 인터페이스](../../winscript/reference/idebugapplicationthreadevents110-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT OnResumeFromBreakPoint( void );  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드에는 매개 변수가 없습니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplicationThreadEvents110 인터페이스](../../winscript/reference/idebugapplicationthreadevents110-interface.md)