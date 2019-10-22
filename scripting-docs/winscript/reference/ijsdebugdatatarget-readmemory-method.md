---
title: 'IJsDebugDataTarget:: ReadMemory 메서드 | Microsoft Docs'
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
ms.openlocfilehash: 84da36433cf3546b34d3e044bb113916c9798117
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572428"
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
 진행 대상 프로세스의 메모리를 읽어올 기본 주소입니다.  
  
 `flags`  
 진행 ReadMemory의 동작을 제어 하는 플래그입니다.  
  
 `pBuffer`  
 제한이 대상 프로세스의 주소 공간에서 콘텐츠를 받는 버퍼입니다. 오류가 발생 하면이 버퍼의 내용이 지정 되지 않습니다.  
  
 `size`  
 진행 프로세스에서 읽을 바이트 수입니다.  
  
 `pBytesRead`  
 제한이 대상 프로세스에서 읽은 바이트 수를 나타냅니다. JsDebugAllowPartialRead가 명확 하 게 설정 된 경우이 값은 항상 입력 크기와 정확 하 게 동일 합니다. JsDebugAllowPartialRead가 지정 된 경우 성공 하면이 값은 0 보다 큽니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 는 성공 시 S_OK를 반환 하 고 오류 코드는 모든 오류에 사용 됩니다. 주소가 유효 하지 않은 경우 E_JsDEBUG_INVALID_MEMORY_ADDRESS를 반환 합니다. 자세한 내용은 JsDebugAllowPartialRead를 참조 하세요.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)