---
title: 'IScriptEntry:: SetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::SetName
ms.assetid: dfa33450-87d7-4c8e-bfd8-0cc2d6542a0e
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d9dfa27c6c8c58c0ee1599e17e1da5b5f424e416
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575349"
---
# <a name="iscriptentrysetname"></a>IScriptEntry::SetName
단일 개체 (예: 함수)를 나타내는 항목의 경우 개체의 이름을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `psz`  
 진행 @No__t_0 개체의 새 이름입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [Iscriptentry 인터페이스](../../winscript/reference/iscriptentry-interface.md)    
 [IScriptEntry::GetName](../../winscript/reference/iscriptentry-getname.md)