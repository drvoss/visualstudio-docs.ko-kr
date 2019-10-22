---
title: IDebugApplication::D ebugOutput | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.DebugOutput
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::DebugOutput
ms.assetid: 6c02939c-3c2d-474a-ab15-49a37e22b4a7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7d52acf0e4b32f0ced63b53a6b37ffe62f1d948e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575011"
---
# <a name="idebugapplicationdebugoutput"></a>IDebugApplication::DebugOutput
지정 된 문자열이 디버거 IDE (통합 개발 환경)에서 표시 되도록 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT DebugOutput(  
   LPCOLESTR  pstr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstr`  
 진행 디버거에 표시할 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드를 사용 하면 언어 엔진에서 언어별 디버깅 출력 지원을 구현할 수 있습니다. 문자열은 일반적으로 디버거의 출력 창에 표시 됩니다.  
  
 이 메서드를 호출 하면 `IApplicationDebugger::onDebugOutput` 호출 됩니다.  
  
## <a name="see-also"></a>참조  
 [Idebugapplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)    
 [IApplicationDebugger::onDebugOutput](../../winscript/reference/iapplicationdebugger-ondebugoutput.md)