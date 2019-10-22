---
title: 'IJsDebugDataTarget:: FreeVirtualMemory 메서드 | Microsoft Docs'
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
ms.openlocfilehash: 835302249e95c89625c07c6d1ef3d7cbaf2905e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577614"
---
# <a name="ijsdebugdatatargetfreevirtualmemory-method"></a>IJsDebugDataTarget::FreeVirtualMemory 메서드
대상 프로세스의 가상 주소 공간 내에서 메모리 영역을 해제 및/또는 커밋 취소 합니다.  
  
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
 진행 메모리를 해제 해야 하는 대상 프로세스 내의 주소입니다.  
  
 `size`  
 진행 커밋을 해제할 때에 대 한 바이트 수입니다. 메모리 영역을 해제 하려면이 값이 0 이어야 합니다.  
  
 `freeType`  
 진행 수행할 사용 가능한 작업 유형을 나타냅니다. 이는 일반적으로 지정 된 페이지 영역을 해제 하는 MEM_RELEASE (0x8000)입니다. 작업 후 페이지는 무료 상태에 있습니다. MEM_DECOMMIT (0x4000)를 대신 사용 하 여 페이지를 해제 하지 않고 커밋을 해제할 때 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 자세한 내용은 VirtualFree Win32 API를 참조 하세요.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)