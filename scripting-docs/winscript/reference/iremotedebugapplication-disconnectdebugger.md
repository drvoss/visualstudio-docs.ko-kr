---
title: IRemoteDebugApplication::D isconnectDebugger | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.DisconnectDebugger
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::DisconnectDebugger
ms.assetid: 989e5a34-0267-4a2e-96b6-e1dcc2ffe883
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89d1f62886aa25fbb130203d36ebd89d6508b393
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572798"
---
# <a name="iremotedebugapplicationdisconnectdebugger"></a>IRemoteDebugApplication::DisconnectDebugger
응용 프로그램에서 현재 디버거의 연결을 끊습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT DisconnectDebugger();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 응용 프로그램에서 현재 디버거의 연결을 끊습니다.  
  
## <a name="see-also"></a>참조  
 [IRemoteDebugApplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md)