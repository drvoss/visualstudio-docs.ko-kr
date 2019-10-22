---
title: 'IDebugDocumentHost:: NotifyChanged | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.NotifyChanged
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::NotifyChanged
ms.assetid: 33a4a54f-3bcb-4422-b3c0-bdbf46590f34
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a4fc0c744887eb3592c4d94c520f33da86812bfc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569179"
---
# <a name="idebugdocumenthostnotifychanged"></a>IDebugDocumentHost::NotifyChanged
문서의 소스 파일이 저장 되었으며 콘텐츠를 새로 고쳐야 함을 호스트에 알립니다.  
  
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
 이 메서드는 문서의 소스 파일이 저장 되었으며 콘텐츠를 새로 고쳐야 함을 호스트에 알립니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentHost 인터페이스](../../winscript/reference/idebugdocumenthost-interface.md)