---
title: 'IEnumJsStackFrames:: Next 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumJsStackFrames.Next
apilocation:
- jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c24ef399a7b12a1bffe8313c09be47d6a6a3b6c8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575527"
---
# <a name="ienumjsstackframesnext-method"></a>IEnumJsStackFrames::Next 메서드
지정 된 수의 프레임을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cFrameCount`  
 진행 가져올 프레임의 수입니다.  
  
 `pFrames`  
 제한이 프레임을 저장할 배열입니다.  
  
 `pcFetched`  
 제한이 반환 되는 프레임의 수입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IEnumJsStackFrames 인터페이스](../../winscript/reference/ienumjsstackframes-interface.md)