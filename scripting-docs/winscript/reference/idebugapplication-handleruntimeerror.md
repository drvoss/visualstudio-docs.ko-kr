---
title: 'IDebugApplication:: HandleRuntimeError | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleRuntimeError
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleRuntimeError
ms.assetid: f8f3bbaf-09e5-4d01-8a35-f380bc7ff8ed
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2fd4ba2b811cd6c4e38c10a0c68c5808f2c0870a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574328"
---
# <a name="idebugapplicationhandleruntimeerror"></a>IDebugApplication::HandleRuntimeError
현재 스레드가 오류에 대 한 알림을 디버거 IDE로 차단 하 고 보냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT HandleRuntimeError(  
   IActiveScriptErrorDebug*  pErrorDebug,  
   IActiveScriptSite*        pScriptSite,  
   BREAKRESUMEACTION*        pbra,  
   ERRORRESUMEACTION*        perra,  
   BOOL*                     pfCallOnScriptError  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pErrorDebug`  
 진행 발생 한 오류입니다.  
  
 `pScriptSite`  
 진행 스레드의 스크립트 사이트입니다.  
  
 `pbra`  
 제한이 디버거가 응용 프로그램을 다시 시작할 때 수행할 동작입니다.  
  
 `perra`  
 제한이 오류가 발생 한 경우 디버거가 응용 프로그램을 다시 시작할 때 수행할 동작입니다.  
  
 `pfCallOnScriptError`  
 제한이 엔진이 `IActiveScriptSite::OnScriptError` 메서드를 호출 해야 하는 경우 `TRUE` 되는 플래그입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 언어 엔진은 런타임 오류를 발생 시키는 스레드의 컨텍스트에서이 메서드를 호출 합니다. 이 메서드는 현재 스레드가 차단 되 고 디버거 IDE로 보낼 오류 알림을 보냅니다. 디버거 IDE에서 응용 프로그램을 다시 시작할 때이 메서드는 수행할 작업을 반환 합니다.  
  
> [!NOTE]
> 런타임 오류 시 스레드는 스택 프레임 열거 또는 식 계산 등의 작업을 수행 하기 위해 언어 엔진을 호출할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [Idebugapplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)    
 [IActiveScriptErrorDebug 인터페이스](../../winscript/reference/iactivescripterrordebug-interface.md)    
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)    
 [BREAKRESUMEACTION 열거형](../../winscript/reference/breakresumeaction-enumeration.md)    
 [ERRORRESUMEACTION 열거형](../../winscript/reference/errorresumeaction-enumeration.md)