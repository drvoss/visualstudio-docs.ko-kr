---
title: DEBUG_TEXT 상수 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: facbdc1258b3fca72a239d9d5cc41772cf577f13
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577364"
---
# <a name="debug_text-constants"></a>DEBUG_TEXT 상수
[Idebugexpressioncontext에서 사용::P arselanguagetext](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## <a name="syntax"></a>구문  
  
```cpp
typedef DWORD DEBUG_TEXT;  
```  
  
## <a name="constants"></a>상수  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|DWORD DEBUG_TEXT_ISEXPRESSION|0x00000001|문이 문이 아닌 식 임을 나타냅니다. 이 플래그는 일부 언어에서 텍스트를 구문 분석 하는 방법에 영향을 줄 수 있습니다.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|반환 값을 사용할 수 있는 경우이 값은 호출자가 사용 합니다.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|의도 하지 않은 결과를 허용 하지 않습니다. 이 플래그가 설정 된 경우 식의 계산은 런타임 상태를 변경 하지 않아야 합니다.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|텍스트를 계산 하는 동안 중단점을 허용 합니다. 이 플래그를 설정 하지 않으면 텍스트를 계산 하는 동안 중단점이 무시 됩니다.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|텍스트를 평가 하는 동안 오류 보고서를 허용 합니다. 이 플래그를 설정 하지 않으면 평가 중에 호스트에 오류가 보고 되지 않습니다.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|식이 식 자체를 실행 하는 대신 코드 컨텍스트로 계산 됨을 나타냅니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)