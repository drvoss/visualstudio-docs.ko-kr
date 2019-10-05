---
title: IActiveScriptGarbageCollector::CollectGarbage | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 75f77c49-2190-4d49-a3e0-9dcf847c502b
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db8683534e449b2cdd8fcdb344c245d93da8fafc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954982"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
액티브 스크립트 호스트는 가비지 수집을 시작 하려면이 메서드를 호출 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>매개 변수  
 `scriptgctype`  
 [in] 합니다 [SCRIPTGCTYPE 열거형](../../winscript/reference/scriptgctype-enumeration.md) 보통 또는 전체 가비지 수집 수행 여부를 지정 하는 합니다.  
  
## <a name="return-value"></a>반환 값  
 HRESULT를 반환합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptGarbageCollector 인터페이스](../../winscript/reference/iactivescriptgarbagecollector-interface.md)