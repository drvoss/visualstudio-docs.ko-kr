---
title: 'IObjectIdentity:: IsEqualObject | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 636dfa07b1fc94dfec2273220aa4101f5cd085b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571468"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
개체가 현재 개체와 같은지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `punk`  
 진행 현재 개체와 비교할 개체의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|개체가 같습니다.|  
|`S_FALSE`|개체가 같지 않습니다.|  
  
## <a name="remarks"></a>주의  
 @No__t_0 메서드의 구현은 개체가 동일한 경우에만 `S_OK`를 반환 해야 합니다.  
  
## <a name="see-also"></a>참조  
 [IObjectIdentity 인터페이스](../../winscript/reference/iobjectidentity-interface.md)