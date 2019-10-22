---
title: 'IDebugApplicationThread110:: IsSuspendedForBreakPoint | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::IsSuspendedForBreakPoint
ms.assetid: 60688222-557f-4a43-a19b-846cee393cd0
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0e70993b95ccffcf6041bb04f37af90667fc4fd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574451"
---
# <a name="idebugapplicationthread110issuspendedforbreakpoint"></a>IDebugApplicationThread110::IsSuspendedForBreakPoint
이 스레드에서 [IDebugApplicationThreadEvents110:: OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md) 가 호출 되었으며 아직 완료 되지 않은 경우를 확인 합니다.  
  
> [!IMPORTANT]
> [IDebugApplicationThread110 인터페이스](../../winscript/reference/idebugapplicationthread110-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT IsSuspendedForBreakPoint([out, annotation("_Out_")] BOOL * pfIsSuspended);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pfIsSuspended`  
 [out] 스레드가 중단점에 대해 일시 중단 되 면 `true`이 고, 그렇지 않으면 `false`입니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplicationThread110 인터페이스](../../winscript/reference/idebugapplicationthread110-interface.md)