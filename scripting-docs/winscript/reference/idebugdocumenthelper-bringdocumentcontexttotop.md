---
title: 'IDebugDocumentHelper:: BringDocumentContextToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.BringDocumentContextToTop
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::BringDocumentContextToTop
ms.assetid: cf9751c5-e9b7-45c6-b084-3f3873dbf01d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63b55844c260f693ab5d89ecd564ed6b6ecd32d6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577012"
---
# <a name="idebugdocumenthelperbringdocumentcontexttotop"></a>IDebugDocumentHelper::BringDocumentContextToTop
이 문서의 컨텍스트를 디버거 사용자 인터페이스의 맨 위로 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pddc`  
 디버거 사용자 인터페이스에서 위쪽으로 가져오기 위한 문서 컨텍스트입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 디버거 사용자 인터페이스의 맨 위에이 문서의 컨텍스트를 가져옵니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentHelper 인터페이스](../../winscript/reference/idebugdocumenthelper-interface.md)