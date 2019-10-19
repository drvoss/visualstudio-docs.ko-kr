---
title: 'IApplicationDebuggerUI:: BringDocumentToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentToTop
ms.assetid: ef5fe1e7-4381-4409-a0d7-58f993abe84e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b51e7b588750fc72e61840c4748c006eea732c22
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577802"
---
# <a name="iapplicationdebuggeruibringdocumenttotop"></a>IApplicationDebuggerUI::BringDocumentToTop
지정 된 디버그 문서를 포함 하는 창을 디버거 사용자 인터페이스의 맨 위에 놓습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT BringDocumentToTop(  
   IDebugDocumentText*  pddt  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pddt`  
 진행 디버거 사용자 인터페이스에서 위쪽으로 가져올 문서를 디버그 합니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_INVALIDARG`|문서를 알 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 지정 된 디버그 문서를 포함 하는 창을 디버거 사용자 인터페이스의 맨 위로 가져옵니다.  
  
## <a name="see-also"></a>참조  
 [IApplicationDebuggerUI 인터페이스](../../winscript/reference/iapplicationdebuggerui-interface.md)