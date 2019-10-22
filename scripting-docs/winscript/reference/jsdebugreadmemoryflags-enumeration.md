---
title: JsDebugReadMemoryFlags 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JsDebugReadMemoryFlags
apilocation:
- jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1757678f20a01221ae46e1535d3190cd463d724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571705"
---
# <a name="jsdebugreadmemoryflags-enumeration"></a>JsDebugReadMemoryFlags 열거형
메모리를 읽을 때의 동작을 지정하는 플래그입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
enum JsDebugReadMemoryFlags{   None = 0,   JsDebugAllowPartialRead= 0x1} JsDebugReadMemoryFlags;  
```  
  
## <a name="members"></a>멤버  
  
### <a name="values"></a>값  
  
|name|설명|  
|----------|-----------------|  
|`JsDebugAllowPartialRead`|메모리의 일부만 성공한 경우 호출자가 읽기 작업을 성공적으로 수행 하려고 함을 나타냅니다. 이를 설정 하는 경우 ' Address '가 유효 하지 않은 경우에만 E_JsDEBUG_INVALID_MEMORY_ADDRESS 오류가 발생 합니다. 이 플래그를 명확 하 게 지정 하면 요청 된 메모리의 일부를 읽을 수 없는 경우 E_JsDEBUG_INVALID_MEMORY_ADDRESS 오류가 발생 합니다.|  
|`None`|호출자가 ReadMemory의 기본 동작을 원한다는 것을 나타냅니다.|  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [Windows 스크립트 인터페이스 참조](../../winscript/reference/windows-script-interfaces-reference.md)