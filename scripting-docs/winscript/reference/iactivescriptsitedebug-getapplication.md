---
title: 'IActiveScriptSiteDebug:: GetApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetApplication
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e2ad81e3b6b1707f5a23271cf0abe3832266c07f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570131"
---
# <a name="iactivescriptsitedebuggetapplication"></a>IActiveScriptSiteDebug::GetApplication
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
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_NOTIMPL`|호스트에서 디버깅을 직접 지원 하지 않습니다.|  
  
## <a name="remarks"></a>주의  
 @No__t_0 메서드는 스마트 호스트가 각 스크립트가 속한 응용 프로그램 개체를 정의 하는 방법을 제공 합니다. 스크립트 엔진은이 메서드를 호출 하 여 포함 하는 응용 프로그램을 가져오고이 작업이 실패 하는 경우에는 `IProcessDebugManager::GetDefaultApplication`을 수행 하려고 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSiteDebug 인터페이스](../../winscript/reference/iactivescriptsitedebug-interface.md)    
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)