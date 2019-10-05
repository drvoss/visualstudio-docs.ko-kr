---
title: 'Ijsdebugdatatarget:: Getthreadcontext 메서드 | Microsoft Docs'
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
ms.openlocfilehash: d7904ef81eb900c6466069267101f30d89e362a1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582835"
---
# <a name="ijsdebugdatatargetgetthreadcontext-method"></a>IJsDebugDataTarget::GetThreadContext 메서드
스레드가 제공 하는 컨텍스트를 검색 합니다.  
  
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
 [in] 대상 프로세스에서 실행 되는 스레드입니다.  
  
 `contextFlags`  
 [in] 상황에 맞는 플래그를 지정합니다. (자세한 내용은 winnt.h에서 context_all 검색)에 대 한 CONTEXT의 ContextFlags 필드와 동일 합니다.  
  
 `contextSize`  
 [in] Pcontext가 지정한 버퍼의 크기입니다.  
  
 `pContext`  
 [out] 플랫폼별 컨텍스트 구조체를 pcontext 지정한 버퍼로 받습니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)