---
title: 'IScriptScriptlet:: SetEventName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.SetEventName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::SetEventName
ms.assetid: 8787d58b-7deb-415b-b0e9-d2f0eb72dcf7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5283646838f02cdc1c5ab27f63fd237d698fc6ed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571902"
---
# <a name="iscriptscriptletseteventname"></a>IScriptScriptlet::SetEventName
Scriptlet와 연결 된 이벤트의 이름을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetEventName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `psz`  
 진행 @No__t_0 개체와 연결 된 이벤트 이름을 포함 하는 버퍼입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IScriptScriptlet 인터페이스](../../winscript/reference/iscriptscriptlet-interface.md)