---
title: 'IRemoteDebugApplication:: ConnectDebugger | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.ConnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::ConnectDebugger
ms.assetid: ded94101-7efe-466f-aa70-b3e30a38c4d8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7ed0ddeffd55475e1be4c9fab1e567d61a4b6654
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572331"
---
# <a name="iremotedebugapplicationconnectdebugger"></a>IRemoteDebugApplication::ConnectDebugger
디버거를이 응용 프로그램에 연결 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ConnectDebugger(  
   IApplicationDebugger*  pad  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pad`  
 진행 이 응용 프로그램에 연결할 디버거입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_FAIL`|디버거가이 응용 프로그램에 이미 연결 되어 있습니다.|  
  
## <a name="remarks"></a>주의  
 응용 프로그램은 한 번에 하나의 디버거만 연결 될 수 있습니다. 디버거가 이미 연결 되어 있으면이 메서드는 실패 합니다.  
  
## <a name="see-also"></a>참조  
 [Iremotedebugapplication:: GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)    
 [IRemoteDebugApplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md)