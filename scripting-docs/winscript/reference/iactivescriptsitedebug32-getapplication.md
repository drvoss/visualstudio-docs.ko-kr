---
title: 'IActiveScriptSiteDebug32:: GetApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 93c4a8fe6e5c2aac8b07f896810dcd03060b46d0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572191"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
이 스크립트 사이트와 연결 된 디버그 응용 프로그램 개체를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppda`  
 제한이 스크립트 사이트와 연결 된 디버그 응용 프로그램 개체에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_NOTIMPL`|호스트에서 디버깅을 직접 지원 하지 않습니다.|  
  
## <a name="remarks"></a>주의  
 `GetApplication` 메서드는 스마트 호스트가 각 스크립트가 속한 응용 프로그램 개체를 정의 하는 방법을 제공 합니다. 스크립트 엔진은이 메서드를 호출 하 여 포함 하는 응용 프로그램을 가져오고이 작업이 실패 하는 경우에는 `IProcessDebugManager::GetDefaultApplication`을 수행 하려고 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptSiteDebug32 인터페이스](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)