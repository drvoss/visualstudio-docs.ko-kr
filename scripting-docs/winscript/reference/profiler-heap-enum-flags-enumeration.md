---
title: PROFILER_HEAP_ENUM_FLAGS 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 17936b7a-40d5-4774-b92b-b24ee391591e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d613ed3bcb4699f20d521f08b6c34d55d8363ba4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62830359"
---
# <a name="profilerheapenumflags-enumeration"></a>PROFILER_HEAP_ENUM_FLAGS 열거형
개체 관계에서 가리킨 힙 개체에 대 한 추가 정보가 있는지 여부를 나타내는 플래그 노출 됩니다. 에 사용 된 [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) 메서드.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_ENUM_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS  = 0x00000001,} PROFILER_HEAP_ENUM_FLAGS;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|값|설명|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_ENUM_FLAGS_NONE|0x00000000|이 힙 개체는 개체 관계에 대 한 추가 정보를 노출 하지 않습니다. 이 힙 개체는 동일한 방식으로 동작 [IActiveScriptProfilerControl3::HeapEnum](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)합니다.|  
|PROFILER_HEAP_ENUM_ENUM_ STORE_RELATIONSHIP_FLAGS|0x00000001|이 힙 개체는 개체 관계에서 지정 된 개체가 getter 또는 setter 메서드인지 여부에 대 한 정보를 노출 합니다. 높은 2 바이트 (16 비트)에 저장할는이 정보는 [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) 중 하나로 필드를 [PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS](../../winscript/reference/profiler-heap-object-relationship-flags-enumeration.md) 열거형 값입니다.|  
|PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|0x00000002|이 힙 개체는 부분 문자열을 올바르게 표시 됩니다.|  
|PROFILER_HEAP_ENUM_FLAGS_RELATIONSHIP_SUBSTRINGS|PROFILER_HEAP_ENUM_FLAGS_STORE_RELATIONSHIP_FLAGS &#124; PROFILER_HEAP_ENUM_FLAGS_SUBSTRINGS|이 힙 개체는 부분 문자열을 올바르게 표시 됩니다.|