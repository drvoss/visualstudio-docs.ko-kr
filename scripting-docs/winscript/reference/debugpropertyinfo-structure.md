---
title: DebugPropertyInfo 구조체 | Microsoft 문서
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
ms.openlocfilehash: 99208626b41f2463178bccecf73c21a1d15fa765
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955265"
---
# <a name="debugpropertyinfo-structure"></a>DebugPropertyInfo 구조체
개체의 이름, 형식 및 값이 있는 계층적 특성을 설명 합니다. 지역 변수, 매개 변수, 조사식 변수 및 식의 디버그 속성을 설명 하는 데 사용 되 고 등록 합니다.  
  
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
 dwValidFields  
 초기화 되는 필드를 지정 하는 데 사용 하는 열거형된 데이터 형식입니다.  
  
 bstrName  
 컨텍스트 내에서 속성 이름입니다.  
  
 bstrType  
 속성 형식, 서식이 지정 된 문자열입니다.  
  
 bstrValue  
 속성 값으로 서식이 지정 된 문자열입니다.  
  
 bstrFullName  
 속성의 전체 이름입니다.  
  
 dwAttrib  
 디버그 속성 특성에 대 한 플래그를 지정 하는 열거형입니다.  
  
 pDebugProp  
 합니다 `IDebugProperty` 이 정보에 설명 된 `DebugPropertyInfo` 구조입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugProperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_ATTRIB_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)