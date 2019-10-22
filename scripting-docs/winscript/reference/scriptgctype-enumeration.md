---
title: SCRIPTGCTYPE 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f289cc7d-2a69-4720-bee0-ea27d054f308
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7fce16c756cf06c8cf01937114402832570a0cd3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574386"
---
# <a name="scriptgctype-enumeration"></a>SCRIPTGCTYPE 열거형
수행할 가비지 수집의 형식입니다. [IActiveScriptGarbageCollector:: CollectGarbage](../../winscript/reference/iactivescriptgarbagecollector-collectgarbage.md) 메서드에서 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef enum tagSCRIPTGCTYPE {    SCRIPTGCTYPE_NORMAL           = 0,    SCRIPTGCTYPE_EXHAUSTIVE       = 1,} SCRIPTGCTYPE;  
```  
  
## <a name="enumeration-values"></a>열거형 값  
  
|||  
|-|-|  
|SCRIPTGCTYPE_NORMAL|정상적인 가비지 수집을 수행 합니다. 정수 값은 0입니다.|  
|SCRIPTGCTYPE_EXHAUSTIVE|과도 한 가비지 수집을 수행 합니다. 정수 값은 1입니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 상수, 열거형 및 오류 코드](../../winscript/reference/active-script-constants-enumerations-and-error-codes.md)