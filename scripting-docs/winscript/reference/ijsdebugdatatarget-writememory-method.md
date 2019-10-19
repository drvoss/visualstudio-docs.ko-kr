---
title: 'IJsDebugDataTarget:: WriteMemory 메서드 | Microsoft Docs'
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
ms.openlocfilehash: 33cd23ad784e222f770dfd5c0e7c2d775aa55e42
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572419"
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
 진행 대상 프로세스의 메모리를 쓸 기본 주소입니다.  
  
 `pMemory`  
 진행 지정 된 프로세스의 주소 공간에 쓸 데이터입니다.  
  
 `size`  
 진행 프로세스에 쓸 바이트 수입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 데이터를 전송 하기 전에 시스템은 기본 주소 및 지정 된 크기의 메모리에 있는 모든 데이터에 대 한 액세스를 액세스할 수 있는지 확인 하 고, 액세스할 수 없는 경우 함수는 E_JsDEBUG_INVALID_MEMORY_ADDRESS 오류를 발생 시킵니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)