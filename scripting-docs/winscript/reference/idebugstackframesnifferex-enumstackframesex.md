---
title: 'IDebugStackFrameSnifferEx:: Enumstack프레임 성 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrameSnifferEx::EnumStackFramesEx
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6a4062e7c0a9b3a82578daffa2ab7ef7e9ba614d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576704"
---
# <a name="idebugstackframesnifferexenumstackframesex"></a>IDebugStackFrameSnifferEx::EnumStackFramesEx
현재 스레드에 대 한 스택 프레임의 열거자를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwSpMin`  
 진행 스택 프레임을 열거 하는 데 필요한 낮은 주소 제한입니다.  
  
 `ppedsf`  
 제한이 현재 스레드에 대 한 스택 프레임의 열거자입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 스택 프레임 열거자는 가장 최근에 푸시한 프레임을 사용 하 여 스택 맨 위에서 시작 되는 프레임을 반환 합니다. 열거자에 `dwSpMin` 보다 크거나 같은 주소를 가진 스택 프레임만 포함 되어 있습니다.  
  
## <a name="see-also"></a>참조  
 [IDebugStackFrameSnifferEx 인터페이스](../../winscript/reference/idebugstackframesnifferex-interface.md)