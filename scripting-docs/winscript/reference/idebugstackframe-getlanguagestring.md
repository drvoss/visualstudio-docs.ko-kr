---
title: 'IDebugStackFrame:: GetLanguageString | Microsoft Docs'
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
ms.openlocfilehash: 83abb038cd8bc018d84cd0c5ddd2a413f8a02248
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576763"
---
# <a name="idebugstackframegetlanguagestring"></a>IDebugStackFrame::GetLanguageString
언어에 대 한 짧은 또는 긴 텍스트 설명을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetLanguageString(  
   BOOL   fLong,  
   BSTR*  pbstrLanguage  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `fLong`  
 진행 플래그 (여기서 `TRUE`는 긴 설명을 반환 하 고 `FALSE`는 간단한 설명을 반환 합니다.  
  
 `pbstrLanguage`  
 제한이 언어에 대 한 설명입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 일반적으로 `fLong` `FALSE` 되는 경우이 메서드는 스택 프레임과 연결 된 언어의 이름만 제공 합니다. @No__t_0 `TRUE` 되는 경우이 방법을 통해 전체 제품 설명을 제공할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [IDebugStackFrame 인터페이스](../../winscript/reference/idebugstackframe-interface.md)