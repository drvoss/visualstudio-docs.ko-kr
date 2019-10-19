---
title: 'IDebugDocumentText:: GetPositionOfLine | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetPositionOfLine
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetPositionOfLine
ms.assetid: d1e6e81b-ddec-4a7c-9b6a-d199e3debfc2
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adf4add99ac41440e6f4daa491b72166e97b5ba5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572106"
---
# <a name="idebugdocumenttextgetpositionofline"></a>IDebugDocumentText::GetPositionOfLine
줄의 첫 번째 문자에 해당 하는 문자 위치를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetPositionOfLine(  
   ULONG   cLineNumber,  
   ULONG*  pcCharacterPosition  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cLineNumber`  
 진행 줄 번호입니다.  
  
 `pcCharacterPosition`  
 제한이 줄의 시작 부분에 있는 문서 내의 문자 위치 `cLineNumber`입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 줄의 첫 번째 문자에 해당 하는 문자 위치를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentText 인터페이스](../../winscript/reference/idebugdocumenttext-interface.md)