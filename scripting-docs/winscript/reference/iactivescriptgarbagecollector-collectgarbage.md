---
title: 'IActiveScriptGarbageCollector:: CollectGarbage | Microsoft Docs'
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
ms.openlocfilehash: 0539ed2cb3540cf33ceaaa15827c3ca08c156698
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573590"
---
# <a name="iactivescriptgarbagecollectorcollectgarbage"></a>IActiveScriptGarbageCollector::CollectGarbage
활성 스크립트 호스트는이 메서드를 호출 하 여 가비지 수집을 시작 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CollectGarbage(        SCRIPTGCTYPE scriptgctype    );  
```  
  
#### <a name="parameters"></a>매개 변수  
 `scriptgctype`  
 진행 정상 또는 철저 한 가비지 수집을 수행할지 여부를 지정 하는 [SCRIPTGCTYPE 열거형](../../winscript/reference/scriptgctype-enumeration.md) 입니다.  
  
## <a name="return-value"></a>반환 값  
 HRESULT를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptGarbageCollector 인터페이스](../../winscript/reference/iactivescriptgarbagecollector-interface.md)