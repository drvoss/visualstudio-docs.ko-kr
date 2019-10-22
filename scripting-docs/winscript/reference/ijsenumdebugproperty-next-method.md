---
title: 'IJsEnumDebugProperty:: Next 메서드 | Microsoft Docs'
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
ms.openlocfilehash: 48c4506d783093395b2d88b7a71d56e3a89d24e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574007"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next 메서드
이 개체의 속성을 읽습니다.  
  
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
 진행 읽을 속성의 수입니다.  
  
 `ppDebugProperty`  
 제한이 속성 브라우저를 나타내는 개체입니다.  
  
 `pActualCount`  
 제한이 개체의 실제 속성 수입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsEnumDebugProperty 인터페이스](../../winscript/reference/ijsenumdebugproperty-interface.md)