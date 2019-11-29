---
title: 'IActiveScriptProfilerCallback2:: OnFunctionExitByName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2::OnFunctionExitByName
ms.assetid: a6ddead4-e66d-4789-b778-84e5c343f908
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a70bc72dd1070759ad8b78e43926f06a2c56ec15
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571629"
---
# <a name="iactivescriptprofilercallback2onfunctionexitbyname"></a>IActiveScriptProfilerCallback2::OnFunctionExitByName
스크립팅 엔진이 DOM (문서 개체 모델) 함수 호출 실행을 완료 했음을 프로파일러 개체에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnFunctionExitByName(  
    [in] [string] const WCHAR *pwszFunctionName,  
    [in] PROFILER_SCRIPT_TYPE scriptType);  
  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pwszFunctionName`  
 진행 스크립팅 엔진의 실행이 완료 된 함수 이름입니다.  
  
 `scriptType`  
 진행 함수의 형식입니다. 유효한 값에 대 한 설명은 [PROFILER_SCRIPT_TYPE 열거](../../winscript/reference/profiler-script-type-enumeration.md)를 참조 하세요.  
  
## <a name="return-value"></a>반환 값  
 이 메서드의 반환 값은 스크립팅 엔진에서 무시 됩니다.  
  
## <a name="remarks"></a>주의  
 DOM 호출의 경우 스크립팅 엔진은 [IActiveScriptProfilerCallback:: OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)를 호출 하는 대신이 메서드를 호출 합니다. 이는 DOM에서 많은 수의 고유한 메서드와 속성 때문입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)   
 [IActiveScriptProfilerCallback2 인터페이스](../../winscript/reference/iactivescriptprofilercallback2-interface.md)