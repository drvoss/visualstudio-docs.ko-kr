---
title: 'IActiveScriptError:: GetExceptionInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptError.GetExceptionInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptError_GetExceptionInfo
ms.assetid: 528416cc-8468-4ad7-a6c2-fa1daf6ecf33
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f776a5f1a60b1280ab1f133ead04fb275782e5c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576937"
---
# <a name="iactivescripterrorgetexceptioninfo"></a>IActiveScriptError::GetExceptionInfo
스크립팅 엔진에서 스크립트를 실행 하는 동안 발생 한 오류에 대 한 정보를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetExceptionInfo(  
    EXCEPINFO *pexcepinfo  // structure for exception information  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pexcepinfo`  
 제한이 오류 정보를 수신 하는 `EXCEPINFO` 구조체의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 `S_OK`을 반환 하 고, 오류가 발생 한 경우 `E_FAIL` 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptError](../../winscript/reference/iactivescripterror.md)