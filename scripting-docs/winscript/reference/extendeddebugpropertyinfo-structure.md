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
ms.openlocfilehash: 09f3c5a219fca9ec9b881e2ae8363aae4d48e03f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575831"
---
# <a name="extendeddebugpropertyinfo-structure"></a>ExtendedDebugPropertyInfo 구조체
확장 속성의 특징을 위한 추가 멤버로 `DebugPropertyInfo` 구조체를 확장 합니다.  
  
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
 초기화할 필드를 지정 하는 데 사용 되는 열거 데이터 형식입니다.  
  
 `bstrName`  
 컨텍스트 내의 속성 이름입니다.  
  
 `bstrType`  
 형식이 지정 된 문자열인 속성 형식입니다.  
  
 `bstrValue`  
 형식이 지정 된 문자열로 된 속성 값입니다.  
  
 `bstrFullName`  
 속성의 전체 이름입니다.  
  
 `dwAttrib`  
 디버그 속성 특성에 대 한 플래그를 지정 하는 열거형입니다.  
  
 `pDebugProp`  
 이 `ExtendedDebugPropertyInfo`에 해당 하 `IDebugProperty` 개체입니다.  
  
 `nDISPID`  
 디스패치 id입니다.  
  
 `nType`  
 확장 속성 형식입니다.  
  
 `varValue`  
 변형에 맞을 수 있는 경우 확장 속성 값입니다.  
  
 `plbValue`  
 속성 값의 실제 데이터 바이트입니다.  
  
 `pDebugExtProp`  
 이 `ExtendedDebugPropertyInfo`에 해당 하 `IDebugExtendedProperty` 개체입니다.  
  
## <a name="see-also"></a>참고 항목  
 [DebugPropertyInfo 구조체](../../winscript/reference/debugpropertyinfo-structure.md)   
 [Idebugproperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)   
 [Idebugextendedproperty 인터페이스](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)