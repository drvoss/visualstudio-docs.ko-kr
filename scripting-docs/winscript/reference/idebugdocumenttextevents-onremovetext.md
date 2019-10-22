---
title: 'IDebugDocumentTextEvents:: onRemoveText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextEvents.onRemoveText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentTextEvents::onRemoveText
ms.assetid: c5dfe674-c42f-4e57-9d48-8380d5aa206b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c302a3b1850db42824f35a306e7e94eaa8a6aa41
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576267"
---
# <a name="idebugdocumenttexteventsonremovetext"></a>IDebugDocumentTextEvents::onRemoveText
문서에서 텍스트가 제거 되었음을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT onRemoveText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToRemove  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cCharacterPosition`  
 진행 제거 된 첫 번째 문자의 문자 위치입니다.  
  
 `cNumToRemove`  
 진행 제거 되는 문자 수입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 문서에서 텍스트가 제거 되었음을 나타냅니다.  
  
## <a name="see-also"></a>참조  
 [Idebugdocumenttextevents 인터페이스](../../winscript/reference/idebugdocumenttextevents-interface.md)    
 [IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)