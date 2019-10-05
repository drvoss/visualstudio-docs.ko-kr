---
title: 액티브 스크립트 Profiler 상수, 열거형 및 구조체 | Microsoft Docs
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
ms.openlocfilehash: 1d39e6feb2cddd0c573368db9bf50b1e77f2e48d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955497"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>액티브 스크립트 프로파일러 상수, 열거형 및 구조체
액티브 스크립트 Profiler 인터페이스에서는 다음 열거를 사용 합니다.  
  
## <a name="constants-enumerations-and-structures"></a>상수, 열거형 및 구조체  
  
|상수|설명|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS 형식](../../winscript/reference/profiler-external-object-address-type.md)|외부 개체 주소 프로파일러입니다. 레지스트리에 [PROFILER_HEAP_OBJECT 구조체](../../winscript/reference/profiler-heap-object-structure.md) 하 고 [PROFILER_HEAP_OBJECT_RELATIONSHIP 구조체](../../winscript/reference/profiler-heap-object-relationship-structure.md)합니다.|  
|[PROFILER_HEAP_OBJECT_ID 형식](../../winscript/reference/profiler-heap-object-id-type.md)|힙 개체의 ID입니다. 에 사용 되는 [PROFILER_HEAP_OBJECT 구조체](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST 구조체](../../winscript/reference/profiler-heap-object-scope-list-structure.md)하십시오 [PROFILER_HEAP_OBJECT_OPTIONAL_INFO 구조체](../../winscript/reference/profiler-heap-object-optional-info-structure.md), 및 [PROFILER_HEAP_OBJECT_RELATIONSHIP 구조체](../../winscript/reference/profiler-heap-object-relationship-structure.md)합니다.|  
|[PROFILER_HEAP_OBJECT_NAME_ID 형식](../../winscript/reference/profiler-heap-object-name-id-type.md)|ID 힙 개체의 이름입니다. 레지스트리에 [PROFILER_HEAP_OBJECT 구조체](../../winscript/reference/profiler-heap-object-structure.md)합니다.|  
  
|열거형|설명|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK 열거형](../../winscript/reference/profiler-event-mask-enumeration.md)|프로 파일링 해야 하는 이벤트의 형식을 나타냅니다.|  
|[PROFILER_HEAP_ENUM_FLAGS 열거형](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|개체 관계에서 가리킨 힙 개체에 대 한 추가 정보가 있는지 여부를 나타내는 플래그 노출 됩니다. 에 사용 된 [IActiveScriptProfilerControl5::EnumHeap2 메서드](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)합니다.|  
|[PROFILER_HEAP_OBJECT_FLAGS 열거형](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|힙 개체에 대 한 기본 정보를 나타내는 플래그입니다. 에 사용 된 [PROFILER_HEAP_OBJECT 구조체](../../winscript/reference/profiler-heap-object-structure.md)합니다.|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE 열거형](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|다양을 한 선택적 정보를 나타냅니다. 레지스트리에 [PROFILER_HEAP_OBJECT_OPTIONAL_INFO 구조체](../../winscript/reference/profiler-heap-object-optional-info-structure.md)합니다.|  
|[PROFILER_RELATIONSHIP_INFO 열거형](../../winscript/reference/profiler-relationship-info-enumeration.md)|관계에서 개체에 대 한 정보를 나타냅니다. 레지스트리에 [PROFILER_HEAP_OBJECT_RELATIONSHIP 구조체](../../winscript/reference/profiler-heap-object-relationship-structure.md)합니다.|  
|[PROFILER_SCRIPT_TYPE 열거형](../../winscript/reference/profiler-script-type-enumeration.md)|스크립트의 유형을 지정합니다.|  
  
|구조체|설명|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT 구조체](../../winscript/reference/profiler-heap-object-structure.md)|힙 개체에서 수집한 나타냅니다 [IActiveScriptProfilerControl3::EnumHeap 메서드](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)합니다.|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO 구조체](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|힙 개체에 대 한 선택적 정보를 나타냅니다.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP 구조체](../../winscript/reference/profiler-heap-object-relationship-structure.md)|힙 개체의 관계를 나타냅니다.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST 구조체](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|힙 개체에 속해 있는 관계의 목록을 나타냅니다.|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST 구조체](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|이 구조는 함수 개체와 연결 합니다. 범위 목록 함수의 클로저를 범위는 각 범위는 각 지정 된 범위에서 변수를 나타내는 연결 된 속성 목록 가진 힙 개체의 목록을 나타냅니다. 경우에 따라 해당 범위에 있는 개체의 이름을 사용할 수 없습니다, 들의 id입니다.|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO 구조체](../../winscript/reference/profiler-property-type-substring-info-structure.md)|부분 문자열의 형식에 대 한 정보를 나타냅니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 프로파일러 인터페이스](../../winscript/reference/active-script-profiler-interfaces.md)