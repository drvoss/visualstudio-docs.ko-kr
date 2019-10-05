---
title: PROFILER_HEAP_OBJECT_OPTIONAL_INFO 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 77e638bd-ae36-4292-a170-90a0c500e610
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c7f28499b5d6e1e01caab1e6fd83fc5ab72ccf6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823868"
---
# <a name="profilerheapobjectoptionalinfo-structure"></a>PROFILER_HEAP_OBJECT_OPTIONAL_INFO 구조체
힙 개체에 대 한 선택적 정보를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_OPTIONAL_INFO{    PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE infoType;    [switch_type(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE), switch_is(infoType)] union    {        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_PROTOTYPE)] PROFILER_HEAP_OBJECT_ID prototype;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_FUNCTION_NAME)] LPCWSTR functionName;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_ATTRIBUTES_SIZE)] UINT elementAttributesSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_ELEMENT_TEXT_CHILDREN_SIZE)] UINT elementTextChildrenSize;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_SCOPE_LIST)] PROFILER_HEAP_OBJECT_SCOPE_LIST* scopeList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INTERNAL_PROPERTY)] PROFILER_HEAP_OBJECT_RELATIONSHIP* internalProperty;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_NAME_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* namePropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_INDEX_PROPERTIES)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* indexPropertyList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_RELATIONSHIPS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* relationshipList;        [case(PROFILER_HEAP_OBJECT_OPTIONAL_INFO_WINRTEVENTS)] PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST* eventList;    };} PROFILER_HEAP_OBJECT_OPTIONAL_INFO;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|형식|설명|  
|------------|----------|-----------------|  
|infoType|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 열거형](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|선택적 정보 형식입니다.|  
|prototype|[PROFILER_HEAP_OBJECT_ID 형식](../../winscript/reference/profiler-heap-object-id-type.md)|힙 개체의 프로토타입 개체의 ID입니다.|  
|functionName|LPCWSTR|힙 개체의 함수 이름입니다.|  
|elementAttributesSize|UINT|힙 개체의 요소 속성의 크기입니다.|  
|elementTextChildrenSize|UINT|힙 개체의 텍스트 자식의 크기입니다.|  
|scopeList|[PROFILER_HEAP_OBJECT_SCOPE_LIST 구조체](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|힙 개체의 범위 목록입니다.|  
|internalProperty|[PROFILER_HEAP_OBJECT_RELATIONSHIP 구조체](../../winscript/reference/profiler-heap-object-relationship-structure.md)|힙 개체의 내부 속성입니다.|  
|namePropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 구조체](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|힙 개체의 이름 속성의 목록입니다.|  
|indexPropertyList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 구조체](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|힙 개체의 인덱스 속성의 목록입니다.|  
|relationshipList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 구조체](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|힙 개체의 관계의 목록입니다.|  
|eventList|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 구조체](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|힙 개체의 이벤트 목록입니다.|