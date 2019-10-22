---
title: 'IRemoteDebugApplication:: CauseBreak | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplication.CauseBreak
apilocation:
- pdm.dll
helpviewer_keywords:
- IRemoteDebugApplication::CauseBreak
ms.assetid: 6a2c27bb-dca0-475c-9918-bdbb70a50d26
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8107d7f8450df759b53175505c8d7fc2b6bde641
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571488"
---
# <a name="iremotedebugapplicationcausebreak"></a>IRemoteDebugApplication::CauseBreak
응용 프로그램이 가능한 한 빨리 디버거로 중단 되도록 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CauseBreak();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드를 호출 하면 응용 프로그램이 즉시 중단 되지 않습니다. 응용 프로그램이 현재 스크립트 코드를 실행 하 고 있지 않은 경우 응용 프로그램이 실제로 중단 되기까지 오랜 시간이 경과할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IRemoteDebugApplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md)