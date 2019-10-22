---
title: 액티브 스크립트 프로파일러 상수, 열거형 및 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a9409799c7da2ed3f4864dea0e7785635492220
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572683"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>액티브 스크립트 프로파일러 상수, 열거형 및 구조체
다음 열거형은 활성 스크립트 프로파일러 인터페이스에서 사용 됩니다.  
  
## <a name="constants-enumerations-and-structures"></a>상수, 열거형 및 구조체  
  
|상수|설명|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS 형식](../../winscript/reference/profiler-external-object-address-type.md)|프로파일러의 외부 개체 주소입니다. [PROFILER_HEAP_OBJECT structure](../../winscript/reference/profiler-heap-object-structure.md) 및 [PROFILER_HEAP_OBJECT_RELATIONSHIP structure](../../winscript/reference/profiler-heap-object-relationship-structure.md)에 사용 됩니다.|  
|[PROFILER_HEAP_OBJECT_ID 형식](../../winscript/reference/profiler-heap-object-id-type.md)|힙 개체의 ID입니다. [PROFILER_HEAP_OBJECT structure](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST Structure](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [PROFILER_HEAP_OBJECT_OPTIONAL_INFO structure](../../winscript/reference/profiler-heap-object-optional-info-structure.md)및 [PROFILER_HEAP_OBJECT_RELATIONSHIP structure](../../winscript/reference/profiler-heap-object-relationship-structure.md)에 사용 됩니다.|  
|[PROFILER_HEAP_OBJECT_NAME_ID 형식](../../winscript/reference/profiler-heap-object-name-id-type.md)|힙 개체의 이름 ID입니다. [PROFILER_HEAP_OBJECT 구조체](../../winscript/reference/profiler-heap-object-structure.md)에 사용 됩니다.|  
  
|열거형|설명|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK 열거형](../../winscript/reference/profiler-event-mask-enumeration.md)|프로 파일링 해야 하는 이벤트 유형을 나타냅니다.|  
|[PROFILER_HEAP_ENUM_FLAGS 열거형](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|개체 관계에서 가리킨 힙 개체에 대 한 추가 정보가 노출 되는지 여부를 나타내는 플래그입니다. [IActiveScriptProfilerControl5:: EnumHeap2 메서드에서](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)사용 됩니다.|  
|[PROFILER_HEAP_OBJECT_FLAGS 열거형](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|힙 개체에 대 한 기본 정보를 나타내는 플래그입니다. [PROFILER_HEAP_OBJECT 구조체](../../winscript/reference/profiler-heap-object-structure.md)에 사용 됩니다.|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 열거형](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|다양 한 종류의 선택적 정보를 나타냅니다. [PROFILER_HEAP_OBJECT_OPTIONAL_INFO 구조체](../../winscript/reference/profiler-heap-object-optional-info-structure.md)에 사용 됩니다.|  
|[PROFILER_RELATIONSHIP_INFO 열거형](../../winscript/reference/profiler-relationship-info-enumeration.md)|관계의 개체에 대 한 정보를 나타냅니다. [PROFILER_HEAP_OBJECT_RELATIONSHIP 구조체](../../winscript/reference/profiler-heap-object-relationship-structure.md)에 사용 됩니다.|  
|[PROFILER_SCRIPT_TYPE 열거형](../../winscript/reference/profiler-script-type-enumeration.md)|스크립트의 유형을 지정 합니다.|  
  
|구조체|설명|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT 구조체](../../winscript/reference/profiler-heap-object-structure.md)|[IActiveScriptProfilerControl3:: Enumheap 메서드에서](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)수집 된 힙 개체를 나타냅니다.|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 구조체](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|힙 개체에 대 한 선택적 정보를 나타냅니다.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP 구조체](../../winscript/reference/profiler-heap-object-relationship-structure.md)|힙 개체의 관계를 나타냅니다.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 구조체](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|힙 개체에 속하는 관계의 목록을 나타냅니다.|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST 구조체](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|이 구조체는 함수 개체에만 연결 됩니다. 범위 목록은 각 범위가 지정 된 각 범위에서 변수를 나타내는 연결 된 속성 목록을 사용 하는 힙 개체인 범위 목록으로 함수에 대 한 클로저를 나타냅니다. 경우에 따라 해당 범위에서 개체의 이름을 사용 하지 못할 수도 있습니다.|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 구조체](../../winscript/reference/profiler-property-type-substring-info-structure.md)|부분 문자열의 형식에 대 한 정보를 나타냅니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 프로파일러 인터페이스](../../winscript/reference/active-script-profiler-interfaces.md)