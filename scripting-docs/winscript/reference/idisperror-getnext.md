---
title: 'IDispError:: GetNext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetNext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetNext
ms.assetid: 3e5267f8-ba62-41c3-bd3e-eced2ad85e8e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81186e6eba7983a1210e5de5bca5d83dd77089da
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573109"
---
# <a name="idisperrorgetnext"></a>IDispError::GetNext
다음 `IDispError` 개체를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetNext(  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppde`  
 제한이 다음 `IDispError` 개체를 지정 합니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 다음 `IDispError` 개체를 검색 합니다. 마지막 `IDispError` 개체인 경우이 메서드는 NULL을 반환 합니다.  
  
> [!NOTE]
> 이 메서드는 구현 되지 않습니다.  
  
## <a name="see-also"></a>참조  
 [IDispError 인터페이스](../../winscript/reference/idisperror-interface.md)