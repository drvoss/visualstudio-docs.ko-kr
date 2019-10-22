---
title: 'IRemoteDebugApplication:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::GetName
ms.assetid: 3a8e8a4b-d7d4-40e5-97a1-f6d18db2e9c4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5689eb9153be0e9b6442ba505d618966f1421d39
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571997"
---
# <a name="iremotedebugapplicationgetname"></a>IRemoteDebugApplication::GetName
이 응용 프로그램 노드의 이름을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetName(  
   BSTR*  pbstrName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrName`  
 제한이 이 응용 프로그램 노드의 이름입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는이 응용 프로그램 노드의 이름을 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IRemoteDebugApplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md)