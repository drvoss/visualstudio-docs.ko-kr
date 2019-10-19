---
title: 'IJsDebugStackWalker:: GetNext 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugStackWalker.GetNext
apilocation:
- jscript9diag.dll
ms.assetid: 0b124768-50d3-4a69-876c-1aa337839a4e
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa667402b46a3404c31dfe26307a5893c68ffcc0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574025"
---
# <a name="ijsdebugstackwalkergetnext-method"></a>IJsDebugStackWalker::GetNext 메서드
다음 프레임을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetNext(  
   IJsDebugFrame **ppFrame  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppFrame`  
 제한이 스택 프레임을 나타내는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 열거할 스택 프레임이 더 이상 없는 경우 E_JsDEBUG_OUTSIDE_OF_VM를 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugStackWalker 인터페이스](../../winscript/reference/ijsdebugstackwalker-interface.md)