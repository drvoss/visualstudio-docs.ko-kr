---
title: IDebugStackFrame::GetLanguageString | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugStackFrame.GetLanguageString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugStackFrame::GetLanguageString
ms.assetid: 561d6306-f214-422f-abc9-b502cbfbe208
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cab0c0ab317754305ca2440748dd680e31750d8a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62934660"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
언어의 단기 또는 장기 텍스트 설명을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `fLong`  
 [in] 플래그를 여기서 `TRUE` 긴 설명을 반환 하 고 `FALSE` 짧은 설명을 반환 합니다.  
  
 `pbstrLanguage`  
 [out] 언어의 설명입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 일반적으로 하는 경우 `fLong` 는 `FALSE`,이 메서드는 스택 프레임과 연결 된 언어의 이름만 제공 합니다. 때 `fLong` 는 `TRUE`,이 메서드는 전체 제품 설명을 제공할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugStackFrame 인터페이스](../../winscript/reference/idebugstackframe-interface.md)