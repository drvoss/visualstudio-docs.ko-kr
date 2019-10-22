---
title: 'Imach가산 Debugmanagercookie:: AddApplication | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.AddApplication
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::AddApplication
ms.assetid: 4d5503c5-aca9-4cf7-9900-f77bf5f3263d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da436308c71a66d3070d42128d8da03ae88d2935
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573907"
---
# <a name="imachinedebugmanagercookieaddapplication"></a>IMachineDebugManagerCookie::AddApplication
응용 프로그램을 실행 중인 응용 프로그램 목록에 추가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD                     dwDebugAppCookie,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pda`  
 진행 응용 프로그램을 실행 중인 응용 프로그램 목록에 표시 합니다.  
  
 `dwDebugAppCookie`  
 진행 디버그 응용 프로그램을 식별 하는 쿠키입니다.  
  
 `pdwAppCookie`  
 제한이 컴퓨터 디버그 관리자에서 응용 프로그램을 제거 하는 데 사용 되는 쿠키입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 `IProcessDebugManager::AddApplication`가 호출 될 때마다 프로세스 디버그 관리자에서 호출 됩니다.  
  
## <a name="see-also"></a>참조  
 [Imachinedebugmanagercookie 인터페이스](../../winscript/reference/imachinedebugmanagercookie-interface.md)    
 [Imachinedebugmanagercookie:: RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)    
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)