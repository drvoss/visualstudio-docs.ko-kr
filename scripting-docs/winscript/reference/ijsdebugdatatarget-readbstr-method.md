---
title: 'IJsDebugDataTarget:: ReadBSTR 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadBSTR
apilocation:
- jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b125f58b4be279eac167b803ed6a683c1fb04ddf
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572445"
---
# <a name="ijsdebugdatatargetreadbstr-method"></a>IJsDebugDataTarget::ReadBSTR 메서드
디버그 대상에서 BSTR을 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `address`  
 진행 읽을 주소입니다.  
  
 `pString`  
 제한이 디버그 대상에서 읽은 BSTR입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 주소가 유효 하지 않은 경우 E_JsDEBUG_INVALID_MEMORY_ADDRESS를 반환 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)