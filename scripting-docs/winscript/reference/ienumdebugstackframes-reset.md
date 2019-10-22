---
title: 'IEnumDebugStackFrames:: Reset | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Reset
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Reset
ms.assetid: 57be2683-5346-4464-bdf5-6fd45b56253a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddd97d60d40eaa15a5ed3e17cc87a0d9ffb197cf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574856"
---
# <a name="ienumdebugstackframesreset"></a>IEnumDebugStackFrames::Reset
열거형 시퀀스를 시작 부분으로 다시 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Reset();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 열거 시퀀스를 시작 부분으로 다시 설정 합니다.  
  
## <a name="see-also"></a>참조  
 [IEnumDebugStackFrames 인터페이스](../../winscript/reference/ienumdebugstackframes-interface.md)