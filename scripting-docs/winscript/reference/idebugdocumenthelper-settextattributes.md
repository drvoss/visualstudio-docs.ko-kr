---
title: 'IDebugDocumentHelper:: SetTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.SetTextAttributes
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::SetTextAttributes
ms.assetid: 31657738-9e4c-436a-be61-23f4185d452e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cc5e5955652fd8b59d4c502e68d97a729ded141
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569467"
---
# <a name="idebugdocumenthelpersettextattributes"></a>IDebugDocumentHelper::SetTextAttributes
텍스트 범위에 대 한 특성을 설정 하 고 해당 텍스트의 다른 특성을 재정의 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetTextAttributes(  
   ULONG              ulCharOffset,  
   ULONG              cChars,  
   SOURCE_TEXT_ATTR*  pstaTextAttr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ulCharOffset`  
 진행 텍스트 범위의 시작 위치입니다.  
  
 `cChars`  
 진행 범위의 문자 수입니다.  
  
 `pstaTextAttr`  
 진행 텍스트 범위에 대 한 소스 텍스트 특성입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 텍스트를 문서에 추가 하기 전에 텍스트 범위에서 `SetTextAttributes`를 호출 하는 것은 오류입니다. @No__t_0, `AddUnicodeText` 또는 `AddDeferredText` 메서드를 호출 하 여 문서에 텍스트를 추가 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentHelper 인터페이스](../../winscript/reference/idebugdocumenthelper-interface.md)    
 [IDebugDocumentHelper:: AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)    
 [IDebugDocumentHelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentHelper:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [SOURCE_TEXT_ATTR 열거형](../../winscript/reference/source-text-attr-enumeration.md)