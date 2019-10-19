---
title: 'IJsDebugProperty:: GetPropertyInfo 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetPropertyInfo
apilocation:
- jscript9diag.dll
ms.assetid: ab9d6e0b-0448-4f21-b0b0-1738867587d2
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf56189c42ef5c696441426191a6850d03ade416
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577311"
---
# <a name="ijsdebugpropertygetpropertyinfo-method"></a>IJsDebugProperty::GetPropertyInfo 메서드
이 개체에 대 한 정보를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetPropertyInfo(  
   UINT nRadix,  
   JsDebugPropertyInfo *pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `nRadix`  
 진행 사용할 기 수입니다.  
  
 `pPropertyInfo`  
 제한이 개체에 대 한 정보입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugProperty 인터페이스](../../winscript/reference/ijsdebugproperty-interface.md)