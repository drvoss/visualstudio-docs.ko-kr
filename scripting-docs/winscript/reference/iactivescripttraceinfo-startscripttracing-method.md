---
title: 'Iactivescripttraceinfo:: Startscripttracing 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 90fac5ed-ce15-49b7-a6f1-605ede6f34e2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b87971e1fd2e484aa54ff4de56ee56e00b19b1e6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62991189"
---
# <a name="iactivescripttraceinfostartscripttracing-method"></a>IActiveScriptTraceInfo::StartScriptTracing 메서드
스크립트 추적을 시작합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT StartScriptTracing(     [in] IActiveScriptSiteTraceInfo * pSiteTraceInfo,     [in] GUID guidContextID );   
```  
  
#### <a name="parameters"></a>매개 변수  
 `pSiteTraceInfo`  
 호스트의 IActiveScriptSiteTraceInfo 포인터입니다.  
  
 `guidContextId`  
 컨텍스트의 GUID입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드에 대 한 가능한 반환 값은 다음과 같습니다.  
  
1. S_OK: 명령 실행 성공  
  
2. E_POINTER: `pSiteTraceInfo` 가 NULL 포인터입니다.  
  
3. E_NOTIMPL: 구현되지 않았습니다.