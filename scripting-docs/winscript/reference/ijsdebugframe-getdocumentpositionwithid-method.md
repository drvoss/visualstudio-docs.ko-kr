---
title: 'IJsDebugFrame:: GetDocumentPositionWithId 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithId
apilocation:
- jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f35f6fb84db95950fe83d571c9f5e5e7db9de1e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573854"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>IJsDebugFrame::GetDocumentPositionWithId 메서드
사용자 수준 문서 내에서이 스택 프레임의 현재 위치를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pDocumentId`  
 제한이 원본 문서의 고유 ID (IDebugDocumentText에 대 한 포인터)입니다.  
  
 `pCharacterOffset`  
 제한이 스크립트의 시작 부분에서 0부터 시작 하는 문자 오프셋입니다.  
  
 `pStatementCharCount`  
 제한이 * PCharacterOffset에서 시작 하는 현재 문의 길이 (문자)입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugFrame 인터페이스](../../winscript/reference/ijsdebugframe-interface.md)