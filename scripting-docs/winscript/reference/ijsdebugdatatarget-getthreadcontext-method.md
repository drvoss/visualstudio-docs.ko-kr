---
title: 'IJsDebugDataTarget:: GetThreadContext 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetThreadContext
apilocation:
- jscript9diag.dll
ms.assetid: faf2a689-6c49-4a7d-b5a6-2b323e2257a7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da5722553b448605129adcf32cfaa52e2dc76352
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577653"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext 메서드
지정 된 스레드의 컨텍스트를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetThreadContext(  
   DWORD threadId,  
   ULONG32 contextFlags,  
   ULONG32 contextSize,  
   void *pContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `threadId`  
 진행 대상 프로세스에서 실행 되는 스레드입니다.  
  
 `contextFlags`  
 진행 컨텍스트 플래그를 지정 합니다. 컨텍스트의 ContextFlags 필드와 같습니다. 자세한 내용은 winnt.exe를 참조 하 고 CONTEXT_ALL를 검색 합니다.  
  
 `contextSize`  
 진행 PContext로 지정 된 버퍼의 크기입니다.  
  
 `pContext`  
 제한이 PContext로 지정 된 버퍼에 플랫폼별 컨텍스트 구조를 수신 합니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)