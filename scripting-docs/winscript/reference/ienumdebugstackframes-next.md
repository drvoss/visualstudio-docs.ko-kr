---
title: 'IEnumDebugStackFrames:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugStackFrames.Next
apilocation:
- jscript.dll
helpviewer_keywords:
- IEnumDebugStackFrames::Next
ms.assetid: ade3f5b0-8ff3-48a0-9433-270789e6d53e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 17261f8ba9b2957d33ed7019c16f2e1423b6b42e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575544"
---
# <a name="ienumdebugstackframesnext"></a>IEnumDebugStackFrames::Next
열거형 시퀀스에서 지정 된 수의 세그먼트를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Next(  
   ULONG                       celt,  
   DebugStackFrameDescriptor*  prgdsfd,  
   ULONG*                      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `celt`  
 진행 검색할 세그먼트 수입니다.  
  
 `prgdsfd`  
 제한이 검색 되는 세그먼트를 나타내는 `DebugStackFrameDescriptor` 인터페이스의 배열을 반환 합니다.  
  
 `pceltFetched`  
 제한이 열거자에서 가져온 실제 세그먼트 수입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 열거형 시퀀스에서 지정 된 수의 세그먼트를 검색 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IEnumDebugStackFrames 인터페이스](../../winscript/reference/ienumdebugstackframes-interface.md)   
 [DebugStackFrameDescriptor 구조체](../../winscript/reference/debugstackframedescriptor-structure.md)