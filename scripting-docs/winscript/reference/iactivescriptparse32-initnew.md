---
title: 'IActiveScriptParse32:: InitNew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c77aa16-f391-4c93-9f1a-4e529a9930b2
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 8b5304d60aed8145e7a68d89b2c6d4386db0d745
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561653"
---
# <a name="iactivescriptparse32initnew"></a>IActiveScriptParse32:: InitNew
스크립팅 엔진을 초기화 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>반환 값  
 성공 하면 `S_OK`을 반환 하 고, 초기화 하는 동안 오류가 발생 한 경우 `E_FAIL` 합니다.  
  
## <a name="remarks"></a>주의  
 스크립팅 엔진을 사용 하려면 먼저 `IPersist*::Load`, `IPersist*::InitNew` 또는 `IActiveScriptParse32::InitNew` 메서드 중 하나를 호출 해야 합니다. 이 메서드의 의미 체계는 `IPersistStreamInit::InitNew`와 동일 합니다. 즉,이 메서드는 스크립팅 엔진 자체를 초기화 하도록 지시 합니다. @No__t_0 또는 `IActiveScriptParse32::InitNew` 및 `IPersist*::Load`를 모두 호출 하는 것은 유효 하지 않으며 `IPersist*::InitNew`, `IActiveScriptParse32::InitNew` 또는 `IPersist*::Load`를 두 번 이상 호출 하는 것은 유효 하지 않습니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptParse32](../../winscript/reference/iactivescriptparse32.md)