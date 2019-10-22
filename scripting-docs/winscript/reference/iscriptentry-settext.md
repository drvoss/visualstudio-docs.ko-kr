---
title: 'IScriptEntry:: SetText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.SetText
apilocation:
- scrobj.dll
helpviewer_keywords:
- ISetEntry::SetText
ms.assetid: 4605481b-7707-43d1-ab78-a9207d0cf6fe
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0b39dcbd2b61e7236403948eaa91a76e0afee45
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573638"
---
# <a name="iscriptentrysettext"></a>IScriptEntry::SetText
@No__t_0 스크립트 블록 또는 `IScriptScriptlet` 이벤트 처리기에 포함 된 소스 코드에 해당 하는 텍스트를 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetText(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `psz`  
 진행 @No__t_0 스크립트 블록의 텍스트 또는 `IScriptScriptlet` 이벤트 처리기의 소스 코드입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IScriptEntry 인터페이스](../../winscript/reference/iscriptentry-interface.md)