---
title: 'IDebugApplicationThread110:: GetActiveThreadRequestCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThread110::GetActiveThreadRequestCount
ms.assetid: 025d2072-1d7f-4448-8aa3-38a014313570
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7f038c1d0958701a14899825a2adb0a11cf604d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574485"
---
# <a name="idebugapplicationthread110getactivethreadrequestcount"></a>IDebugApplicationThread110::GetActiveThreadRequestCount
현재 처리 중인 PDM 스레드 전환 메커니즘의 스레드 요청 수를 반환 합니다. 이 값은 일반적으로 0 또는 1입니다. 그러나 한 스레드 호출이 처리를 시작했지만 스레드를 동기적으로 호출하거나 스레드를 일시 중단하고 들어오는 호출을 다시 처리할 수 있는 경우 (예: 디버거 스레드에서 발급 된 [IRemoteDebugApplicationEvents Interface](../../winscript/reference/iremotedebugapplicationevents-interface.md)를 사용 하는 경우) 숫자가 더 높을 수 있습니다.  
  
> [!IMPORTANT]
> [IDebugApplicationThread110 인터페이스](../../winscript/reference/idebugapplicationthread110-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetActiveThreadRequestCount([out, annotation("_Out_")] UINT * puiThreadRequests);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `puiThreadRequests`  
 제한이 스레드 요청 수입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugApplicationThread110 인터페이스](../../winscript/reference/idebugapplicationthread110-interface.md)