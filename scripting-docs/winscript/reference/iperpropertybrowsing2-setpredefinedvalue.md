---
title: 'IPerPropertyBrowsing2:: SetPredefinedValue | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.SetPredefinedValue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::SetPredefinedValue
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1a823a04082b7e19b2c1bc475c1070cc501789e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576238"
---
# <a name="iperpropertybrowsing2setpredefinedvalue"></a>IPerPropertyBrowsing2::SetPredefinedValue
@No__t_0 지정 된 속성의 값을 설정 합니다. 미리 정의 된 값은 토큰으로 식별 됩니다 `dwCookie.`  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dispid`  
 진행 미리 정의 된 값이 설정 되는 속성의 디스패치 식별자입니다.  
  
 `dwCookie`  
 진행 설정할 값을 식별 하는 토큰입니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT` (일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IPerPropertyBrowsing2 인터페이스 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)