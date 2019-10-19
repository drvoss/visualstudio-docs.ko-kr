---
title: 'IDebugProperty:: SetValueAsString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.SetValueAsString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::SetValueAsString
ms.assetid: cad8d7b2-19a5-4a29-9000-cafdecdc238b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67e12652056442d9ac162be7af3a0d9e2b61b82c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574935"
---
# <a name="idebugpropertysetvalueasstring"></a>IDebugProperty::SetValueAsString
지정 된 문자열에서 속성 값을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetValueAsString (  
   LPCOLESTR pszValue,  
   UINTnRadix,  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszValue`  
 진행 설정할 값입니다.  
  
 `nRadix`  
 진행 숫자 정보를 해석 하는 데 사용할 기 수입니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT` (일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugProperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)