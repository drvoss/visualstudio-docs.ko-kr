---
title: 'IDebugDocumentText:: GetSize | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetSize
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetSize
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef6f75b396dddec80fb2ae89c71f8579ce3c29b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572086"
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
문서에서 줄 수와 문자 수를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pcNumLines`  
 제한이 문서의 줄 수입니다. 이 매개 변수가 NULL 이면 메서드는 값을 반환 하지 않습니다.  
  
 `pcNumChars`  
 제한이 문서에 있는 문자 수입니다. 이 매개 변수가 NULL 이면 메서드는 값을 반환 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 문서에서 줄 수와 문자 수를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentText 인터페이스](../../winscript/reference/idebugdocumenttext-interface.md)