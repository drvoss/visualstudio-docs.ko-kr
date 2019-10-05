---
title: 'Ijsdebugdatatarget:: Freevirtualmemory 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.FreeVirtualMemory
apilocation:
- jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bf450c03d996a47f9dcd00899ddee46b75d6df32
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62583043"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory 메서드
릴리스 및/또는 대상 프로세스의 가상 주소 공간 내의 메모리 영역을 커밋 해제  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `address`  
 [in] 여기서는 메모리를 해제 해야 하는 대상 프로세스 내의 주소입니다.  
  
 `size`  
 [in] 커밋 해제할 바이트 수입니다. 메모리 영역을 해제 하려면이 값이 0 이어야 합니다.  
  
 `freeType`  
 [in] 수행 하려는 사용 가능한 작업 유형을 나타냅니다. 이것이 일반적으로 MEM_RELEASE(0X8000), 페이지의 지정된 된 영역을 릴리스 하는입니다. 작업 후, 페이지는 사용 가능한 상태가 됩니다. MEM_DECOMMIT (0x4000)를 해제 하지 않고 페이지 커밋 해제 대신 사용할 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>설명  
 추가 정보는 VirtualFree Win32 API를 참조 하세요.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)