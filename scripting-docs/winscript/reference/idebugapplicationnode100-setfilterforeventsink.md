---
title: 'IDebugApplicationNode100:: SetFilterForEventSink | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f85241bee7b35d40bf193a613a6fefda4265be6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574730"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
특정 [Idebugapplicationnodeevents 인터페이스](../../winscript/reference/idebugapplicationnodeevents-interface.md) 구현에 대 한 필터를 설정 합니다. 이를 통해 스크립트 디버거는 컴파일러에서 생성 된 자식 응용 프로그램 노드를 필터링 하 여 해당 노드를 만들거나 제거할 때 더 이상 이벤트를 전송 하지 않습니다. 기본적으로 모든 노드가 전송 됩니다.  
  
> [!IMPORTANT]
> [IDebugApplicationNode100 인터페이스](../../winscript/reference/idebugapplicationnode100-interface.md) 는 PDM v 10.0 이상에서 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwCookie`  
 필터의 쿠키입니다.  
  
 `filter`  
 필터입니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplicationNode100 인터페이스](../../winscript/reference/idebugapplicationnode100-interface.md)