---
title: 'IActiveScriptError:: GetSourcePosition | Microsoft Docs'
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
ms.openlocfilehash: 76ed307f988a3e5bf77ff978c466eda6e5dfee18
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576892"
---
# <a name="iactivescripterrorgetsourceposition"></a>IActiveScriptError::GetSourcePosition
스크립팅 엔진에서 스크립트를 실행 하는 동안 오류가 발생 한 소스 코드의 위치를 검색 합니다.  
  
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
 제한이 컨텍스트를 식별 하는 쿠키를 받는 변수의 주소입니다. 이 매개 변수의 해석은 호스트 응용 프로그램에 따라 달라 집니다.  
  
 `pulLineNumber`  
 제한이 오류가 발생 한 소스 파일의 줄 번호를 받는 변수의 주소입니다.  
  
 `pichCharPosition`  
 제한이 오류가 발생 한 줄에서 문자 위치를 받는 변수의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 `S_OK`을 반환 하 고 위치가 검색 되지 않은 경우 `E_FAIL`을 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)