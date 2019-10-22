---
title: 'IActiveScriptProfilerControl:: StartProfiling 파일링 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProfilerControl.StartProfiling
apilocation:
- scrobj.dll
ms.assetid: 56a7b3b7-8c21-43d0-9d8b-53bbc19fabb9
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cfc59dd43ac3eed433f92af2cdd0aefe40392c4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571577"
---
# <a name="iactivescriptprofilercontrolstartprofiling"></a>IActiveScriptProfilerControl::StartProfiling
스크립팅 엔진에서 프로 파일링을 시작 합니다. 스크립팅 엔진은 [CoCreateInstance](https://docs.microsoft.com/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance)를 호출 하 여 프로파일러 개체의 인스턴스를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT StartProfiling(  
    [in] REFCLSID clsidProfilerObject,  
    [in] DWORD dwEventMask,  
    [in] DWORD dwContext);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `clsidProfilerObject`  
 진행 만들 프로파일러 개체의 CLSID (클래스 식별자)입니다.  
  
 `dwEventMask`  
 진행 이벤트 유형을 지정 하는 4 바이트 비트 마스크입니다. 비트는 [PROFILER_EVENT_MASK 열거형](../../winscript/reference/profiler-event-mask-enumeration.md)에 정의 되어 있습니다.  
  
 `dwContext`  
 진행 프로파일러 개체에 전달 되는 4 바이트 값입니다.  
  
## <a name="return-value"></a>반환 값  
 HRESULT를 반환 합니다. 다음과 같은 값을 사용할 수 있습니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|메서드가 성공했으며|  
|`ACTIVPROF_E_PROFILER_PRESENT`|프로 파일링이 이미 사용 하도록 설정 되어 있습니다.|  
  
## <a name="see-also"></a>참조  
 [IActiveScriptProfilerControl 인터페이스](../../winscript/reference/iactivescriptprofilercontrol-interface.md)