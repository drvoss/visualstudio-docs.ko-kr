---
title: 'Ijsdebugdatatarget:: Allocatevirtualmemory 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.AllocateVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c04bf21882ec39054c74f060eaa2c6f65ac0b4d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583069"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory 메서드
예약 및/또는 커밋 대상 프로세스의 가상 주소 공간 내의 메모리 영역입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `address`  
 [in] 메모리를 커밋하거나 예약 대상 프로세스 내의 주소입니다. 일반적으로이 값은 0 인 경우 시스템에는 주소를 선택 합니다.  
  
 `size`  
 [in] 할당할 바이트 메모리 영역의 크기입니다. 시스템은 자동으로 다음 페이지 경계로 올림 됩니다.  
  
 `allocationType`  
 [in] 수행 하려는 할당 유형을 나타냅니다. 이 MEM_COMMIT 일반적으로 &#124; 예약 및 할당 한 번에 커밋하는 MEM_RESERVE (0x3000).  
  
 `pageProtection`  
 [in] 할당할 페이지 영역에 대 한 메모리 보호 합니다. 페이지가 커밋되는 경우 메모리 보호 상수 (예: PAGE_READWRITE, PAGE_EXECUTE) 중 하나를 지정할 수 있습니다.  
  
 `pAllocatedAddress`  
 [out] 할당 된 페이지 영역의 기준 주소입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>설명  
 함수는 MEM_RESET를 사용 하지 않으면 0으로 할당 된 메모리를 초기화 합니다. 추가 정보는 VirtualAlloc Win32 API를 참조 하세요.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)