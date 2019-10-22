---
title: 'IDebugDocumentText:: GetLineOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetLineOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetLineOfPosition
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8ce32e46c42ee864a88e169a79539efb8b05633
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572120"
---
# <a name="idebugdocumenttextgetlineofposition"></a>IDebugDocumentText::GetLineOfPosition
줄 번호를 반환 하 고, 지정 된 문자 위치에 해당 하는 줄 내에서 문자 오프셋을 선택적으로 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cCharacterPosition`  
 진행 문자 위치 범위의 시작 위치입니다.  
  
 `pcLineNumber`  
 제한이 범위의 줄 번호입니다.  
  
 `pcCharacterOffsetInLine`  
 [in, out] 줄 `pcLineNumber` 내 범위의 문자 오프셋입니다. 이 매개 변수를 `NULL` 하는 경우이 메서드는 값을 반환 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 줄 번호를 반환 하 고, 지정 된 문자 위치에 해당 하는 줄 내에서 문자 오프셋을 선택적으로 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentText 인터페이스](../../winscript/reference/idebugdocumenttext-interface.md)