---
title: 'IDebugDocumentText:: GetContextOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetContextOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetContextOfPosition
ms.assetid: 86560853-d9b1-499a-a1b5-ea06aa1f1f5c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6a35a85a6e4761e1bd0db67caafd0913e7e28a3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572146"
---
# <a name="idebugdocumenttextgetcontextofposition"></a>IDebugDocumentText::GetContextOfPosition
제공 된 문자 위치 범위에 해당 하는 문서 컨텍스트 개체를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetContextOfPosition(  
   ULONG                    cCharacterPosition,  
   ULONG                    cNumChars,  
   IDebugDocumentContext**  ppsc  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cCharacterPosition`  
 진행 문자 위치 범위의 시작 위치입니다.  
  
 `cNumChars`  
 진행 범위의 문자 수입니다.  
  
 `ppsc`  
 제한이 지정 된 문자 위치 범위에 해당 하는 문서 컨텍스트 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 제공 된 문자 위치 범위에 해당 하는 문서 컨텍스트 개체를 만듭니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentText 인터페이스](../../winscript/reference/idebugdocumenttext-interface.md)