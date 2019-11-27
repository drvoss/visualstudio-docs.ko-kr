---
title: 'IDebugExtendedProperty:: GetExtendedPropertyInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::GetExtendedPropertyInfo
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77167c46e02bcf2bf5d3ce5836ad5de103176e93
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576382"
---
# <a name="idebugextendedpropertygetextendedpropertyinfo"></a>IDebugExtendedProperty::GetExtendedPropertyInfo
확장 속성에 대 한 확장 된 정보를 페치합니다 .이는 보다 간단한 `IDebugProperty`보다 자세한 정보를 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwFieldSpec`  
 진행 `ExtendedDebugPropertyInfo` 구조에서 입력할 필드를 결정 하는 EX_DBGPROP_INFO_FLAGS 상수를 지정 합니다.  
  
 `nRadix`  
 진행 숫자 정보를 해석 하는 데 사용할 기 수입니다.  
  
 `pExtendedPropertyInfo`  
 제한이 속성을 설명 하는 `ExtendedDebugPropertyInfo` 구조체를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT`(일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Idebugextendedproperty 인터페이스](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo 구조체](../../winscript/reference/extendeddebugpropertyinfo-structure.md)