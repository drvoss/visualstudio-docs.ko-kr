---
title: DebugPropertyInfo 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DebugPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- DebugPropertyInfo structure
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 793c83b467460f0744abffe3f161f7510f56257a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575063"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo 구조체
이름, 형식 및 값을 포함 하는 계층적 특성의 개체를 설명 합니다. 이 메서드는 지역 변수, 매개 변수, 조사식 변수 및 식의 디버그 속성을 설명 하 고 등록 하는 데 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## <a name="members"></a>멤버  
 Dw유효한 필드  
 초기화할 필드를 지정 하는 데 사용 되는 열거 데이터 형식입니다.  
  
 bstrName  
 컨텍스트 내의 속성 이름입니다.  
  
 bstrType  
 형식이 지정 된 문자열인 속성 형식입니다.  
  
 bstrValue  
 형식이 지정 된 문자열로 된 속성 값입니다.  
  
 bstrFullName  
 속성의 전체 이름입니다.  
  
 dwAttrib  
 디버그 속성 특성에 대 한 플래그를 지정 하는 열거형입니다.  
  
 pDebugProp  
 이 `DebugPropertyInfo` 구조의 정보에서 설명 하는 `IDebugProperty`입니다.  
  
## <a name="see-also"></a>참조  
 [Idebugproperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)    
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)    
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)