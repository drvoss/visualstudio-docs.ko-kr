---
title: 'Ijsenumdebugproperty:: Next 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsEnumDebugProperty.Next
apilocation:
- jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ec6a1dded8c24de06a5746261a19b6609a97ada
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977541"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next 메서드
이 개체에 대 한 속성을 읽습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `count`  
 [in] 읽을 속성 수입니다.  
  
 `ppDebugProperty`  
 [out] 속성 브라우저를 나타내는 개체입니다.  
  
 `pActualCount`  
 [out] 개체의 속성의 실제 수입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [IJsEnumDebugProperty 인터페이스](../../winscript/reference/ijsenumdebugproperty-interface.md)