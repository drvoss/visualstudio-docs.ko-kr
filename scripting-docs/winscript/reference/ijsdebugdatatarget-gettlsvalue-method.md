---
title: 'IJsDebugDataTarget:: GetTlsValue 메서드 | Microsoft Docs'
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
ms.openlocfilehash: eecf9acf370656d5310a03d68ed74e10671a0bc2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577598"
---
# <a name="ijsdebugdatatargetgettlsvalue-method"></a>IJsDebugDataTarget::GetTlsValue 메서드
디버깅 중인 스레드의 경우 지정 된 TLS 인덱스의 TLS (스레드 로컬 저장소) 슬롯에서 값을 검색 합니다.  
  
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
 진행 읽을 대상 프로세스에서 실행 되는 스레드입니다.  
  
 `tlsIndex`  
 진행 대상 프로세스에서 TlsAlloc 함수를 호출할 때 할당 된 TLS 인덱스입니다.  
  
 `pValue`  
 제한이 스레드의 TLS 슬롯에 저장 된 포인터 크기 값입니다. 대상 스레드가 32 비트 이면이 값의 위쪽 32 비트는 0이 됩니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 프로세스의 각 스레드에는 각 TLS 인덱스에 대 한 고유한 슬롯이 있습니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)