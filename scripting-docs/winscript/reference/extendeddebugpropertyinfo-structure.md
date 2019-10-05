---
title: ExtendedDebugPropertyInfo 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ExtendedDebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- ExtendedDebugPropertyInfo structure
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fe0eef00d2bf064a8a002925f4ba5607d36f31c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955188"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo 구조체
확장 된 `DebugPropertyInfo` 확장된 속성을 특성화 하기 위한 추가 멤버를 사용 하 여 구조입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## <a name="members"></a>멤버  
 `dwValidFields`  
 초기화 되는 필드를 지정 하는 데 사용 하는 열거형된 데이터 형식입니다.  
  
 `bstrName`  
 컨텍스트 내에서 속성 이름입니다.  
  
 `bstrType`  
 속성은 형식이 지정 된 문자열로 입력 합니다.  
  
 `bstrValue`  
 서식이 지정 된 문자열 속성 값입니다.  
  
 `bstrFullName`  
 속성의 전체 이름입니다.  
  
 `dwAttrib`  
 디버그 속성 특성에 대 한 플래그를 지정 하는 열거형입니다.  
  
 `pDebugProp`  
 `IDebugProperty` 여기에 해당 하는 개체 `ExtendedDebugPropertyInfo`합니다.  
  
 `nDISPID`  
 디스패치 id입니다.  
  
 `nType`  
 확장된 속성 형식입니다.  
  
 `varValue`  
 확장된 속성 값 변형에 맞출 수 있습니다.  
  
 `plbValue`  
 속성 값의 실제 데이터 바이트입니다.  
  
 `pDebugExtProp`  
 `IDebugExtendedProperty` 여기에 해당 하는 개체 `ExtendedDebugPropertyInfo`합니다.  
  
## <a name="see-also"></a>참고 항목  
 [DebugPropertyInfo 구조체](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty 인터페이스](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)