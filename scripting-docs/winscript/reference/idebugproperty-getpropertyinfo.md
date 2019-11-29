---
title: 'IDebugProperty:: GetPropertyInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0698e09cd9643322a237a81d971248577fd97e0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562334"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
메서드나 인덱싱된 속성을 설명 하는 `IDebugProperty` 값을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwFields`  
 진행 `DebugPropertyInfo` 구조에서 입력할 필드를 결정 하는 `DBGPROP_INFO_FLAGS` 상수를 지정 합니다.  
  
 `nRadix`  
 진행 숫자 정보의 서식을 지정 하는 데 사용할 기 수입니다.  
  
 `pPropertyInfo`  
 제한이 속성을 설명 하는 `DebugPropertyInfo` 구조체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT`(일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Idebugproperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [DebugPropertyInfo 구조체](../../winscript/reference/debugpropertyinfo-structure.md)