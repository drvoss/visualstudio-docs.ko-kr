---
title: 'IApplicationDebugger:: QueryAlive | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.QueryAlive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 867d00a4ef42aa8759496540edc1937fc6f2a0a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577822"
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
디버거가 응답 하는지 여부를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 디버거가 응답 하는지 여부를 나타냅니다. 이 메서드의 구현은 항상 `S_OK`을 반환 해야 합니다.  
  
 디버거 프로세스가 예기치 않게 종료 되 면 COM은이 메서드에 대 한 호출에 대 한 마샬링 프록시에서 오류를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IApplicationDebugger 인터페이스](../../winscript/reference/iapplicationdebugger-interface.md)