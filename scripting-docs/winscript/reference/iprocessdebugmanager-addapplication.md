---
title: 'IProcessDebugManager:: AddApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.AddApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::AddApplication
ms.assetid: 73828299-11eb-4c58-ad70-f80f2d0eede8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ad8132b9b51efa5f5c2f260e48441e5da64c42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576807"
---
# <a name="iprocessdebugmanageraddapplication"></a>IProcessDebugManager::AddApplication
컴퓨터 디버그 관리자의 실행 중인 응용 프로그램 목록에 응용 프로그램을 추가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pda`  
 진행 실행 중인 응용 프로그램 목록에 추가할 디버그 응용 프로그램입니다.  
  
 `pdwAppCookie`  
 제한이 컴퓨터 디버그 관리자에서 응용 프로그램을 제거 하는 데 사용 되는 쿠키입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 컴퓨터 디버그 관리자의 실행 중인 응용 프로그램 목록에 응용 프로그램을 추가 합니다.  
  
## <a name="see-also"></a>참조  
 [Iprocessdebugmanager 인터페이스](../../winscript/reference/iprocessdebugmanager-interface.md)    
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)