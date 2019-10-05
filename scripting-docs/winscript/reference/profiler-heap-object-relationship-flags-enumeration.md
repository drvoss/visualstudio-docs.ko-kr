---
title: PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1a41b642-c9a9-4d83-b943-d59b232eebf6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 322f6f3352c1b0dfad4572d55e1ebe2388c8cc4a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823636"
---
# <a name="profilerheapobjectrelationshipflags-enumeration"></a>PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 열거형
개체 관계에서 가리킨 힙 개체가 있는지 여부를 나타내는 플래그는 getter 또는 setter 메서드입니다. 에 사용 합니다 [EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) 변수에 PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS 값이 지정 된 경우 메서드는 `enumFlags` 매개 변수입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE                      = 0x00000000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR           = 0x00010000,    PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR           = 0x00020000,} PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|값|설명|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_NONE|0x00000000|개체 관계에서 가리킨 힙 개체가 getter 또는 setter 메서드로 식별 되지 됩니다.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_GET_ACCESSOR|0x00010000|개체 관계에서 가리킨 힙 개체는 getter 메서드입니다. 이 정보는의 높은 2 바이트 (16 비트)에 저장 되어야 합니다 [PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo](../../winscript/reference/profiler-heap-object-relationship-structure.md) 필드입니다.|  
|PROFILER_HEAP_OBJECT_RELATIONSHIP_FLAGS_IS_SET_ACCESSOR|0x00020000|개체 관계에서 가리킨 힙 개체는 setter 메서드입니다. 이 정보는의 높은 2 바이트 (16 비트)에 저장 될는 `PROFILER_HEAP_OBJECT_RELATIONSHIP.relationshipInfo` 필드입니다.|