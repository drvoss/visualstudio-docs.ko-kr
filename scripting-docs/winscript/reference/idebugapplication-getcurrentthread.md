---
title: 'IDebugApplication:: GetCurrentThread | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.GetCurrentThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::GetCurrentThread
ms.assetid: 15128e77-6fc6-42a2-8c04-20e22ef03f29
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6d0f95ee5b45e974c1f0fb38ea25edb1175dbbd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574949"
---
# <a name="idebugapplicationgetcurrentthread"></a>IDebugApplication::GetCurrentThread
현재 실행 중인 스레드와 연결 된 스레드를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetCurrentThread(  
   IDebugApplicationThread**  pat  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pat`  
 제한이 현재 실행 중인 스레드와 연결 된 스레드입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 현재 실행 중인 스레드와 연결 된 스레드를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)