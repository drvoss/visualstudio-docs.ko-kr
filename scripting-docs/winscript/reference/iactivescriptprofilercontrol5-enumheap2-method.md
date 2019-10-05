---
title: IActiveScriptProfilerControl5::EnumHeap2 메서드 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: a25859eb-ac28-4a97-bcb3-33788982a76b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c90c536dee76d67fdb93dd205e8f6eedff6dcc7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992941"
---
# <a name="iactivescriptprofilercontrol5enumheap2-method"></a>IActiveScriptProfilerControl5::EnumHeap2 메서드
인터페이스를 반환 합니다 ([IActiveScriptProfilerHeapEnum 인터페이스](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)) 연관된 된 스크립트 엔진의 컨텍스트에서 GC 힙 개체에서 반복을 사용할 수 있는 합니다.  
  
 디버그에서이 메서드를 호출 하거나 릴리스 모드 수 있습니다. UI 스레드가 유휴 상태일 때이 메서드를 호출 해야 합니다. 제외 하 고 스크립트 엔진에 대 한 없는 작업을 수행 하는 메서드를 호출한 후 [iactivescriptprofilerheapenum:: Next 메서드](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md) 때까지 [iactivescriptprofilerheapenum:: Next 메서드](../../winscript/reference/iactivescriptprofilerheapenum-next-method.md)S_FALSE를 반환 합니다. 또는 [IActiveScriptProfilerHeapEnum 인터페이스](../../winscript/reference/iactivescriptprofilerheapenum-interface.md) 인터페이스 포인터가 릴리스될 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT EnumHeap2(    [in] PROFILER_HEAP_ENUM_FLAGS enumFlags,    [out] IActiveScriptProfilerHeapEnum** ppEnum);  
```  
  
#### <a name="parameters"></a>매개 변수  
 enumFlags  
 개체 관계에서 가리킨 개체에 대 한 추가 정보 노출 되는지 여부를 지정 하는 값입니다. 추가 정보는 가리키는 개체가 getter 또는 setter 메서드인지 여부를 나타낼 수 있습니다. 자세한 내용은 참조 하세요. [PROFILER_HEAP_ENUM_FLAGS 열거형](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)합니다.  
  
 ppEnum  
 [out] 반환 된 [IActiveScriptProfilerHeapEnum 인터페이스](../../winscript/reference/iactivescriptprofilerheapenum-interface.md)합니다.  
  
## <a name="return-value"></a>반환 값  
 HRESULT를 반환합니다. 다음과 같은 값을 사용할 수 있습니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공적으로 완료 힙 열거형입니다.|  
|`E_OUTOFMEMORY`|메모리가 힙 열거를 수행할 수 없습니다.|  
|`E_FAIL`|내부 오류가 발생했습니다.|