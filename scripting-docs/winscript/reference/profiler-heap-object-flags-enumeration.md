---
title: PROFILER_HEAP_OBJECT_FLAGS 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 0f517743-cc4a-4911-add3-a43680071a1f
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7fde5ed275691d78e534cd7b8d8e958a8f20325
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823840"
---
# <a name="profilerheapobjectflags-enumeration"></a>PROFILER_HEAP_OBJECT_FLAGS 열거형
힙 개체에 대 한 기본 정보를 나타내는 플래그입니다. 에 사용 된 [PROFILER_HEAP_OBJECT 구조체](../../winscript/reference/profiler-heap-object-structure.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef [v1_enum] enum {    PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT            = 0x00000001,    PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT               = 0x00000002,    PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED           = 0x00000004,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL              = 0x00000008,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN      = 0x00000010,    PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH     = 0x00000020,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE      = 0x00000040,    PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE      = 0x00000080,    PROFILER_HEAP_OBJECT_FLAGS_NEW_STATE_UNAVAILABLE = 0x00000100,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE        = 0x00000200,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS    = 0x00000400,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE        = 0x00000800,    PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE       = 0x00001000,} PROFILER_HEAP_OBJECT_FLAGS;  
```  
  
## <a name="members"></a>멤버  
  
|멤버|값|설명|  
|------------|-----------|-----------------|  
|PROFILER_HEAP_OBJECT_FLAGS_NEW_OBJECT|0x00000001|이 힙 개체는 이전 힙 열거형 요청 이후 할당 되었습니다. [PROFILER_HEAP_OBJECT_ID 형식](../../winscript/reference/profiler-heap-object-id-type.md) 개체가 수집 되는 경우 값을 다시 사용할 수 있습니다.|  
|PROFILER_HEAP_OBJECT_FLAGS_IS_ROOT|0x00000002|이 힙 개체는 개체 그래프의 루트 개체가입니다.|  
|PROFILER_HEAP_OBJECT_FLAGS_SITE_CLOSED|0x00000004|닫힌 스크립트 사이트에서이 힙 개체는입니다.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL|0x00000008|이 힙 개체는 외부 JavaScript 가비지 컬렉션 힙에 할당 되었습니다.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_UNKNOWN|0x00000010|이 힙 개체는 외부 IUnknown 구현 하 고 가비지 컬렉션 힙에 할당 되었습니다.|  
|PROFILER_HEAP_OBJECT_FLAGS_EXTERNAL_DISPATCH|0x00000020|이 힙 개체는 외부 가비지 컬렉션 힙에 할당 된 하 고 IDISPATCH 인터페이스를 구현 합니다.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_APPROXIMATE|0x00000040|이 힙 개체의 크기는 근사치입니다.|  
|PROFILER_HEAP_OBJECT_FLAGS_SIZE_UNAVAILABLE|x00000080|이 힙 개체의 크기를 사용할 수 없는 경우|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_INSTANCE|0x00000200|힙 개체는 Windows 런타임 인스턴스입니다.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_RUNTIMECLASS|0x00000400|힙 개체는 Windows 런타임 런타임 클래스입니다.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_DELEGATE|0x00000800|힙 개체는 Windows 런타임 대리자입니다.|  
|PROFILER_HEAP_OBJECT_FLAGS_WINRT_NAMESPACE|0x00001000|힙 개체는 Windows 런타임 네임 스페이스입니다.|