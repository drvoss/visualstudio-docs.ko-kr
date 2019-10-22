---
title: 'IDebugDocumentText:: GetPositionOfContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetPositionOfContext
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetPositionOfContext
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da759eb98a6cdd28066ddaa8aafe785ede337a6e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572124"
---
# <a name="idebugdocumenttextgetpositionofcontext"></a>IDebugDocumentText::GetPositionOfContext
문서 컨텍스트에 해당 하는 문자 위치 범위를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `psc`  
 진행 문서 컨텍스트 개체입니다.  
  
 `pcCharacterPosition`  
 제한이 문자 위치 범위의 시작 위치입니다.  
  
 `cNumChars`  
 제한이 범위의 문자 수입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드에 제공 된 문서 컨텍스트가이 문서와 연결 되어 있어야 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentText 인터페이스](../../winscript/reference/idebugdocumenttext-interface.md)