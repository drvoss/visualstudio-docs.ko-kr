---
title: 'IJsDebugFrame:: GetDocumentPositionWithName 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithName
apilocation:
- jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b818ca4dc1ec4402973026668972507861c86f22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575116"
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName 메서드
사용자 수준 문서 내에서이 스택 프레임의 현재 위치를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pDocumentName`  
 제한이 정적 스크립트의 경우 문서에 대 한 URL입니다. 동적 스크립트의 경우 스크립트 유형 (예: eval 코드, 함수 코드 등)을 포함 하는 이름이 반환 됩니다.  
  
 `pLine`  
 [out] 문서 내에서 1부터 줄의 줄 위치입니다.  
  
 `pColumn`  
 [out] 문서 내에서 1부터 줄의 줄 위치입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugFrame 인터페이스](../../winscript/reference/ijsdebugframe-interface.md)