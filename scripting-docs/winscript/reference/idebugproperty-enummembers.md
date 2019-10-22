---
title: 'IDebugProperty:: EnumMembers | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5f8c5f2cbb107d55e9ffe602cb7d3492701de10c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562426"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
속성의 멤버를 열거 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwFieldSpec`  
 진행 채울 열거 된 디버그 속성 구조의 필드를 결정 하는 `DBGPROP_INFO_FLAGS` 상수를 지정 합니다.  
  
 `nRadix`  
 진행 숫자 정보를 해석 하는 데 사용할 기 수입니다.  
  
 `refiid`  
 진행 이 IID는 열거자를 필터링 하기 위해 전달 됩니다. IID는 `IDebugPropertyEnumType_All`에서 상속 하는 `IDebugPropertyEnumType` 인터페이스 중 하나입니다.  
  
 `ppEnum`  
 제한이 멤버 속성을 열거 하는 `IEnumDebugPropertyInfo` 인터페이스를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT` (일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [Idebugproperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)    
 [IDebugPropertyEnumType_All 인터페이스](../../winscript/reference/idebugpropertyenumtype-all-interface.md)    
 [IEnumDebugPropertyInfo 인터페이스](../../winscript/reference/ienumdebugpropertyinfo-interface.md)