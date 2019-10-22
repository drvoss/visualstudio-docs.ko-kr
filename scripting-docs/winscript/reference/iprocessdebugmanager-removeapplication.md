---
title: 'IProcessDebugManager:: RemoveApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.RemoveApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::RemoveApplication
ms.assetid: 334e869d-81ae-4d30-9e89-89763ad4f184
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d079d9089dbc47ac272388c680fa585a3532eea8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576531"
---
# <a name="iprocessdebugmanagerremoveapplication"></a>IProcessDebugManager::RemoveApplication
응용 프로그램을 실행 중인 응용 프로그램 목록에서 제거 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT RemoveApplication(  
   DWORD  dwAppCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwAppCookie`  
 진행 응용 프로그램이 응용 프로그램 목록에 추가 될 때 `IProcessDebugManager::AddApplication`에서 제공 하는 쿠키입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 실행 중인 응용 프로그램 목록에서 응용 프로그램을 제거 합니다.  
  
## <a name="see-also"></a>참조  
 [Iprocessdebugmanager:: AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)    
 [IProcessDebugManager 인터페이스](../../winscript/reference/iprocessdebugmanager-interface.md)