---
title: 'Ijsdebugdatatarget:: Writememory 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.WriteMemory
apilocation:
- jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 622de16cc5f755c5d69059a0e0f28d881121861c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558179"
---
# <a name="ijsdebugdatatargetwritememory-method"></a>IJsDebugDataTarget::WriteMemory 메서드
대상 프로세스의 메모리를 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `address`  
 [in] 대상 프로세스의 메모리를 작성 하는 기본 주소입니다.  
  
 `pMemory`  
 [in] 지정된 된 프로세스의 주소 공간에 쓸 데이터입니다.  
  
 `size`  
 [in] 프로세스에 쓸 바이트의 수입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>설명  
 데이터 전송이 발생 하기 전에 시스템에는 기본 주소와 지정된 된 크기의 메모리에서 모든 데이터 쓰기 권한으로 액세스할 수 있고 액세스할 수 없는 경우 함수는 E_JsDEBUG_INVALID_MEMORY_ADDRESS 오류를 발생 시킵니다 확인 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)