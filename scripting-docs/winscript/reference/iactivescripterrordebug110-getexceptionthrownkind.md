---
title: 'IActiveScriptErrorDebug110:: GetExceptionThrownKind | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110::QueryIsFirstChance
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d50ef1dfa3492fdc43a5010b624dae296c692722
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575049"
---
# <a name="iactivescripterrordebug110getexceptionthrownkind"></a>IActiveScriptErrorDebug110::GetExceptionThrownKind
Throw된 예외의 종류를 나타내는 값을 반환합니다.  
  
> [!IMPORTANT]
> [IActiveScriptErrorDebug110 인터페이스](../../winscript/reference/iactivescripterrordebug110-interface.md) 는 PDM 버전 11.0 이상에서 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pExceptionKind`  
 제한이 [SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 열거형](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md) 열거형 값으로 표시 되는 throw 되는 예외 종류 (예: 첫 번째 또는 처리 되지 않은 예외)입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="see-also"></a>참조  
 [IActiveScriptErrorDebug110 인터페이스](../../winscript/reference/iactivescripterrordebug110-interface.md)