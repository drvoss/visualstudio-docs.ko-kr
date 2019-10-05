---
title: IDebugDocumentText::GetSize | Microsoft Docs
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
ms.openlocfilehash: 95f8df44a503fa72f57a9cee17eb5e832e4eb670
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008594"
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
문서의 줄 번호 및 문자 수를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pcNumLines`  
 [out] 문서의 줄 수입니다. 이 매개 변수가 NULL 인 경우 메서드는 값을 반환 하지 않습니다.  
  
 `pcNumChars`  
 [out] 문서의 문자 수입니다. 이 매개 변수가 NULL 인 경우 메서드는 값을 반환 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 이 메서드는 문서의 줄 번호 및 문자 수를 반환합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugDocumentText 인터페이스](../../winscript/reference/idebugdocumenttext-interface.md)