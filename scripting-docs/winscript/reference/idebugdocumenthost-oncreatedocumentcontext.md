---
title: 'IDebugDocumentHost:: OnCreateDocumentContext | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.OnCreateDocumentContext
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::OnCreateDocumentContext
ms.assetid: 080c8604-cfd7-484e-a337-15040870e683
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3fdfa64f66288cba47dec7c498db15238e55f954
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569116"
---
# <a name="idebugdocumenthostoncreatedocumentcontext"></a>IDebugDocumentHost::OnCreateDocumentContext
새 문서 컨텍스트가 생성 중임을 호스트에 알리고, 호스트에서 필요에 따라 새 컨텍스트에 대 한 알 수 없는 제어를 반환할 수 있도록 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT OnCreateDocumentContext(  
   IUnknown**  ppunkOuter  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ppunkOuter`  
 제한이 새 컨텍스트를 제어 하는 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_NOTIMPL`|호스트에서 제어 개체를 제공 하지 않습니다.|  
  
## <a name="remarks"></a>주의  
 호스트는이 메서드를 사용 하 여 도우미 제공 문서 컨텍스트에 새 기능을 추가할 수 있습니다. 이 메서드는 **E_NOTIMPL** 또는 null 외부 개체를 반환할 수 있으며,이 경우 호출자는 컨텍스트를 만들어야 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentHost 인터페이스](../../winscript/reference/idebugdocumenthost-interface.md)