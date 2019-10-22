---
title: 'IScriptEntry:: SetBody | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetBody
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1af865c8366481204ee413377a083b09d8c97383
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575378"
---
# <a name="iscriptentrysetbody"></a>IScriptEntry::SetBody
@No__t_0 스크립트 블록 또는 `IScriptScriptlet` scriptlet의 본문에 있는 텍스트를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `psz`  
 진행 @No__t_0 스크립트 블록의 경우 스크립트 태그에 포함 된 텍스트를 `psz` 합니다.  
  
 @No__t_0 함수 블록의 경우 함수 본문은 `psz`입니다.  
  
 @No__t_1에서 파생 되는 `IScriptScriptlet` 개체의 경우는 scriptlet의 스크립트 텍스트 `psz`입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [Iscriptentry 인터페이스](../../winscript/reference/iscriptentry-interface.md)    
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)