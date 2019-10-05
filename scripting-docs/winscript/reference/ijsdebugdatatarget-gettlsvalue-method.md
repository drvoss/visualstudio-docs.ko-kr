---
title: 'Ijsdebugdatatarget:: Gettlsvalue 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.GetTlsValue
apilocation:
- jscript9diag.dll
ms.assetid: db575be9-7b24-45c5-9008-e4f2f76d6757
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 458aaab05f274983fdaf69c6e702502974665403
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582812"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue 메서드
디버깅 중인 스레드의 지정된 된 TLS 인덱스에 대 한 스레드 로컬 저장소 (TLS) 슬롯에서 값을 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetTlsValue(  
   DWORD threadId,  
   UINT32 tlsIndex,  
   UINT64 *pValue  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `threadId`  
 [in] 읽을 대상 프로세스에서 실행 되는 스레드입니다.  
  
 `tlsIndex`  
 [in] 대상 프로세스 TlsAlloc 함수가 호출 될 때 할당 된 TLS 인덱스입니다.  
  
 `pValue`  
 [out] 스레드의 TLS 슬롯에 저장 된 포인터 크기의 값입니다. 대상 스레드가 32 비트 이면이 값의 상위 32 비트는 0이 됩니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>설명  
 각 스레드는 프로세스는 각 TLS 인덱스에 대 한 자체 슬롯을 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)