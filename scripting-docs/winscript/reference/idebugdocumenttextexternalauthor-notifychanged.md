---
title: 'IDebugDocumentTextExternalAuthor:: NotifyChanged | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentTextExternalAuthor.NotifyChanged
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentTextExternalAuthor::NotifyChanged
ms.assetid: f0de7984-3a15-49e2-bd29-f768f34d2a4d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ad02db80bd24a8a5ba96abaa61e85be9d69e553e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575950"
---
# <a name="idebugdocumenttextexternalauthornotifychanged"></a>IDebugDocumentTextExternalAuthor::NotifyChanged
문서 소스가 변경 되었음을 호스트에 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT NotifyChanged();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 문서 소스가 변경 되었음을 호스트에 알리기 위해 파일 기반 디버거 문서를 수정 하 고 저장 한 후 외부 편집기에서 호출 됩니다. 그런 다음 호스트는 소스 파일에서 문서를 새로 고칩니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentTextExternalAuthor 인터페이스](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)