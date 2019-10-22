---
title: 'IDebugSessionProviderEx: StartDebugSession | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugSessionProviderEx:StartDebugSession
apilocation:
- scrobj.dll
ms.assetid: 247337ca-476c-4aa7-8500-d84fd1d98176
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfe26265d56b2179feeac2a9802940258074b1c7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574305"
---
# <a name="idebugsessionproviderexstartdebugsession"></a>IDebugSessionProviderEx:StartDebugSession
지정 된 응용 프로그램을 사용 하 여 디버그 세션을 시작 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT StartDebugSession(  
   IRemoteDebugApplication*  pda  
   BOOL  fQuery  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pda`  
 진행 디버그 응용 프로그램을 지정 합니다.  
  
 `fQuery`  
 진행 True는 쿼리를 나타냅니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 지정 된 응용 프로그램을 사용 하 여 디버그 세션을 시작 합니다. 이 호출에서 반환 하기 전에 디버거가 `IRemoteDebugApplication::ConnectDebugger`를 호출 해야 합니다.  
  
## <a name="see-also"></a>참조  
 [Idebugsessionproviderex 인터페이스](../../winscript/reference/idebugsessionproviderex-interface.md)    
 [IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)