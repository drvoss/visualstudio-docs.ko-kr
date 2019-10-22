---
title: 'IDebugApplicationThreadEvents110:: OnSuspendForBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
ms.assetid: 224245ac-2aa2-43ae-97ed-493afc3d0122
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5d73d7769dd48889a75da63da64be1d2977a088
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573340"
---
# <a name="idebugapplicationthreadevents110onsuspendforbreakpoint"></a>IDebugApplicationThreadEvents110::OnSuspendForBreakPoint
스레드가 중단점에 대해 완전히 일시 중단 되었으며 아직 정상적인 실행을 다시 시작 하지 않는지 여부를 확인 합니다.  
  
> [!IMPORTANT]
> [IDebugApplicationThreadEvents110 인터페이스](../../winscript/reference/idebugapplicationthreadevents110-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT OnSuspendForBreakPoint( void );  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드에는 매개 변수가 없습니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplicationThreadEvents110 인터페이스](../../winscript/reference/idebugapplicationthreadevents110-interface.md)