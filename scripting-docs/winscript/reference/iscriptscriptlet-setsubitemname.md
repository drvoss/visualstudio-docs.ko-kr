---
title: 'IScriptScriptlet:: SetSubItemName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.SetSubItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::SetSubItemName
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ab4f7afec9302126ccbfcbe7f2abafc74cbf17d6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571851"
---
# <a name="iscriptscriptletsetsubitemname"></a>IScriptScriptlet::SetSubItemName
Scriptlet 개체 호스트의 정규화 된 이름에서 마지막 식별자를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `psz`  
 호스트의 정규화 된 scriptlet 이름에 둘 이상의 수준이 있는 경우 `psz`은 두 번째 수준에서 식별자의 버퍼 주소입니다.  
  
 호스트의 정규화 된 scriptlet 이름에 수준이 하나 있는 경우 `psz`는 첫 번째 수준에서 식별자의 버퍼 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IScriptScriptlet 인터페이스](../../winscript/reference/iscriptscriptlet-interface.md)