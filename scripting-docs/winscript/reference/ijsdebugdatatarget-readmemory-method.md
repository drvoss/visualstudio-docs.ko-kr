---
title: 'Ijsdebugdatatarget:: Readmemory 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadMemory
apilocation:
- jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 705fff3bf2d4be78897c18c5a4c61bd74a8c2230
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62582360"
---
# <a name="ijsdebugdatatargetreadmemory-method"></a>IJsDebugDataTarget::ReadMemory 메서드
대상 프로세스의 메모리를 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `address`  
 [in] 대상 프로세스의 메모리를 읽을 수 있는 기본 주소입니다.  
  
 `flags`  
 [in] ReadMemory 동작을 제어 하는 플래그입니다.  
  
 `pBuffer`  
 [out] 대상 프로세스의 주소 공간에서 콘텐츠를 받는 버퍼입니다. 오류가 발생 하면이 버퍼의 내용을 지정 되지 않습니다.  
  
 `size`  
 [in] 프로세스에서 읽을 바이트 수입니다.  
  
 `pBytesRead`  
 [out] 대상 프로세스에서 읽은 바이트 수를 나타냅니다. JsDebugAllowPartialRead가 선택 취소 하는 경우 성공 시이 값은 항상 입력된 크기와 정확히 동일 합니다. JsDebugAllowPartialRead가 지정 된, 성공 하면이 값은 0 보다 커야 합니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>설명  
 성공 및 오류 코드 반환 s_ok이 고, 모든 오류에 사용 됩니다. 주소가 올바르지 않으면 E_JsDEBUG_INVALID_MEMORY_ADDRESS를 반환 합니다. 자세한 내용은 JsDebugAllowPartialRead를 참조 하십시오.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)