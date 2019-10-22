---
title: JS_PROPERTY_ATTRIBUTES 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_ATTRIBUTES
apilocation:
- jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94a72228e1ad6ab49568f3291ad9add7209ef3da
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571740"
---
# <a name="js_property_attributes-enumeration"></a>JS_PROPERTY_ATTRIBUTES 열거형
속성의 특성을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>멤버  
  
|name|설명|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|속성에 특성이 없습니다.|  
|`JS_PROPERTY_HAS_CHILDREN`|속성에 자식 요소가 있습니다.|  
|`JS_PROPERTY_FAKE`|속성은 "[method]"와 같은 가짜 노드를 나타냅니다.|  
|`JS_PROPERTY_METHOD`|속성은 메서드입니다.|  
|`JS_PROPERTY_READONLY`|속성이 읽기 전용입니다.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|속성은 네이티브 WinRT 개체에 대한 포인터입니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [Windows 스크립트 인터페이스 참조](../../winscript/reference/windows-script-interfaces-reference.md)