---
title: 'IDebugApplication:: FCanJitDebug | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FCanJitDebug
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FCanJitDebug
ms.assetid: d7ddac65-4864-411f-bf66-34a46c03f239
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d68240ffd86935e9936642c09d5131f70b46e9ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576872"
---
# <a name="idebugapplicationfcanjitdebug"></a>IDebugApplication::FCanJitDebug
JIT (just-in-time) 디버거가 등록 되었는지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
BOOL FCanJitDebug();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드가 성공 하 고 JIT 디버거가 등록 된 경우 메서드는 `TRUE` 반환 합니다. 그 외의 경우 `FALSE`를 반환합니다.  
  
## <a name="remarks"></a>주의  
 이 메서드는 JIT 디버거가 등록 되었는지 여부를 확인 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)