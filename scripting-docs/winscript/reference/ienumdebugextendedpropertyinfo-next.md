---
title: 'IEnumDebugExtendedPropertyInfo:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumDebugExtendedPropertyInfo.Next
apilocation:
- scrobj.dll
helpviewer_keywords:
- IEnumDebugExtendedPropertyInfo::Next
ms.assetid: ac41c9a3-19d1-4596-8a87-01c10b131be3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 23ebc3e3fd1f7802f4630be42a594d73f8657e43
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574267"
---
# <a name="ienumdebugextendedpropertyinfonext"></a>IEnumDebugExtendedPropertyInfo::Next
열거형 시퀀스에서 지정 된 수의`ExtendedDebugPropertyInfo` 구조체를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Next (  
   ULONGcelt,  
   ExtendedDebugPropertyInfo *rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `celt`  
 진행 검색할 `ExtendedDebugPropertyInfo`구조체의 수입니다.  
  
 `rgelt`  
 제한이 검색 된 `ExtendedDebugPropertyInfo` 구조체의 배열입니다.  
  
 `pceltFetched`  
 제한이 실제로 검색 된 `ExtendedDebugPropertyInfo` 구조체의 수입니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT`(일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IEnumDebugExtendedPropertyInfo 인터페이스](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 구조체](../../winscript/reference/extendeddebugpropertyinfo-structure.md)