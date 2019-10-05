---
title: IMachineDebugManager::AddApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManager.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 96c1b865c722a3cceab331b81b1204ee682b911f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977850"
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
응용 프로그램을 실행 하는 추가 응용 프로그램 목록입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pda`  
 [in] 응용 프로그램을 실행 하는 응용 프로그램 목록입니다.  
  
 `pdwAppCookie`  
 [out] 컴퓨터 디버그 관리자에서 응용 프로그램을 제거 하는 데 사용 되는 쿠키입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 프로세스 디버그 관리자에서이 메서드는 때마다 `IProcessDebugManager::AddApplication` 라고 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IMachineDebugManager 인터페이스](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)