---
title: 'IActiveScriptAuthor:: RemoveNamedItem | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.RemoveNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::RemoveNamedItem
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cade532d2ca276237981855cafe12804307d0bb6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572846"
---
# <a name="iactivescriptauthorremovenameditem"></a>IActiveScriptAuthor::RemoveNamedItem
스크립트 작성 엔진의 네임 스페이스에서 `NamedItem` 개체를 제거 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszName`  
 진행 제거할 `NamedItem` 개체를 식별 하는 버퍼의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`S_FALSE`|`NamedItem` 개체가 스크립트 작성 엔진의 네임 스페이스에 없습니다.|  
  
## <a name="remarks"></a>주의  
 [IActiveScript:: AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 은 스크립트 작성 엔진의 네임 스페이스에 `NamedItem` 개체를 삽입 하는 데 사용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)