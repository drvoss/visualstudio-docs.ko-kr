---
title: 'IProcessDebugManager:: CreateDebugDocumentHelper | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IProcessDebugManager.CreateDebugDocumentHelper
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::CreateDebugDocumentHelper
ms.assetid: d644e192-1bcc-4768-a91e-239cd920adcd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a009fa5174ab897116c02b91e376e2dc41d67600
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577100"
---
# <a name="iprocessdebugmanagercreatedebugdocumenthelper"></a>IProcessDebugManager::CreateDebugDocumentHelper
이 응용 프로그램에 대 한 새 디버그 문서 도우미를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CreateDebugDocumentHelper(  
   IUnknown*               punkOuter,  
   IDebugDocumentHelper**  pddh  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `punkOuter`  
 진행 반환 된 개체를 집계할 경우 `punkOuter`는 제어 `IUnknown`에 대 한 인터페이스 포인터입니다. 그렇지 않으면 null 포인터입니다.  
  
 `pddh`  
 제한이 이 응용 프로그램에 대 한 디버그 문서 도우미 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는이 응용 프로그램에 대 한 새 디버그 문서 도우미를 만듭니다.  
  
## <a name="see-also"></a>참조  
 [IProcessDebugManager 인터페이스](../../winscript/reference/iprocessdebugmanager-interface.md)