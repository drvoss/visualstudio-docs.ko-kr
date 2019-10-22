---
title: JS_PROPERTY_MEMBERS 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_MEMBERS
apilocation:
- jscript9diag.dll
ms.assetid: 3b870e5c-5518-4073-8384-f0c9c1777d9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3645e95859e2c2b785e01c7ee9a3cbee8155138d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571722"
---
# <a name="js_property_members-enumeration"></a>JS_PROPERTY_MEMBERS 열거형
개체의 멤버에 대한 요청에 반환할 정보의 유형을 지정하는 플래그입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
enum JS_PROPERTY_MEMBERS{   JS_PROPERTY_MEMBERS_ALL = 0,   JS_PROPERTY_MEMBERS_ARGUMENTS = 1} JS_PROPERTY_MEMBERS;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="values"></a>값  
  
|name|설명|  
|----------|-----------------|  
|`JS_PROPERTY_MEMBERS_ALL`|모든 멤버를 열거하는 요청을 나타냅니다.|  
|`JS_PROPERTY_MEMBERS_ARGUMENTS`|인수에만 열거하는 요청을 나타냅니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [Windows 스크립트 인터페이스 참조](../../winscript/reference/windows-script-interfaces-reference.md)