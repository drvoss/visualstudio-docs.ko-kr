---
title: 'Iactivescriptparse:: Initnew | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.InitNew
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_InitNew
ms.assetid: 3a582bd6-fc0d-43a5-812f-5ea55a8517a1
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55d38031708694aa777f7598f261afdfc2b4f3b9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009322"
---
# <a name="iactivescriptparseinitnew"></a>IActiveScriptParse::InitNew
스크립팅 엔진을 초기화합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT InitNew(void);  
```  
  
## <a name="return-value"></a>반환 값  
 반환 `S_OK` 성공 하면 또는 `E_FAIL` 초기화 하는 동안 오류가 발생 합니다.  
  
## <a name="remarks"></a>설명  
 스크립팅 엔진을 사용 하려면 먼저 다음 방법 중 하나를 호출 해야 합니다. `IPersist*::Load`, `IPersist*::InitNew`, 또는 `IActiveScriptParse::InitNew`합니다. 이 메서드의 의미 체계는 동일 `IPersistStreamInit::InitNew`이 메서드의 지시에 따라 스크립팅 엔진 자체 초기화에 해당 합니다. 둘 다를 호출할 수는 `IPersist*::InitNew` 또는 `IActiveScriptParse::InitNew` 하 고 `IPersist*::Load`를 호출할 것도 `IPersist*::InitNew`, `IActiveScriptParse::InitNew`, 또는 `IPersist*::Load` 두 번 이상.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)