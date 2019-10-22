---
title: 'IJsDebugDataTarget:: AllocateVirtualMemory 메서드 | Microsoft Docs'
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
ms.openlocfilehash: 30ad8a3eb277823271fbfb4c2e10364b8602775c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577638"
---
# <a name="ijsdebugdatatargetallocatevirtualmemory-method"></a>IJsDebugDataTarget::AllocateVirtualMemory 메서드
대상 프로세스의 가상 주소 공간 내에서 메모리 영역을 예약 및/또는 커밋합니다.  
  
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
 진행 메모리를 커밋하거나 예약 해야 하는 대상 프로세스 내의 주소입니다. 이 값은 일반적으로 0 이며,이 경우 시스템에서 주소를 선택 합니다.  
  
 `size`  
 진행 할당할 메모리 영역의 크기 (바이트)입니다. 시스템이 자동으로 다음 페이지 경계로 올림 됩니다.  
  
 `allocationType`  
 진행 수행할 할당 유형을 나타냅니다. 이는 일반적으로 &#124; 한 단계로 할당을 예약 하 고 커밋하는 0X3000 (MEM_COMMIT MEM_RESERVE)입니다.  
  
 `pageProtection`  
 진행 할당할 페이지의 영역에 대 한 메모리 보호입니다. 페이지를 커밋하는 경우 메모리 보호 상수 (예: PAGE_READWRITE, PAGE_EXECUTE) 중 하나를 지정할 수 있습니다.  
  
 `pAllocatedAddress`  
 제한이 할당 된 페이지 영역의 기준 주소입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 MEM_RESET를 사용 하지 않는 경우 함수는 할당 하는 메모리를 0으로 초기화 합니다. 자세한 내용은 VirtualAlloc Win32 API를 참조 하세요.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)