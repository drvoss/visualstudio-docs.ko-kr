---
title: IActiveScriptError::GetSourcePosition | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetSourcePosition
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetSourcePosition
ms.assetid: ae9b26b1-82a7-4645-9686-3261d8248664
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4446235a9584bc45fad84b6f92ecc02592e554f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009626"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
스크립팅 엔진을 스크립트를 실행 하는 동안 오류가 발생 하는 소스 코드의 위치를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetSourcePosition(  
    DWORD *pdwSourceContext,  // context cookie  
    ULONG *pulLineNumber,     // line number of error  
    LONG *pichCharPosition    // character position of error  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pdwSourceContext`  
 [out] 컨텍스트를 식별 하는 쿠키를 받는 변수의 주소입니다. 이 매개 변수의 해석은 호스트 응용 프로그램에 따라 달라 집니다.  
  
 `pulLineNumber`  
 [out] 오류가 발생 한 원본 파일의 줄 번호를 받는 변수의 주소입니다.  
  
 `pichCharPosition`  
 [out] 오류가 있는 줄의 문자 위치를 받는 변수의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 반환 `S_OK` 성공 하면 또는 `E_FAIL` 경우 위치를 검색 하지 못했습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)