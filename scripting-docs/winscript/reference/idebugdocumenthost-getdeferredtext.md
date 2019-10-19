---
title: 'IDebugDocumentHost:: GetDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetDeferredText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetDeferredText
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 273b4eb52b7263d34c347dff3a00479945b809df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569428"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
원래 호스트 문서에서 `IDebugDocumentHelper::AddDeferredText` 메서드를 사용 하 여 추가 된 문자 범위를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwTextStartCookie`  
 진행 텍스트의 시작 위치를 나타내는 호스트 정의 쿠키입니다.  
  
 `pcharText`  
 [in, out] 문자 텍스트 버퍼입니다. 이 매개 변수가 `NULL` 않는 경우이 메서드는 문자를 반환 하지 않습니다.  
  
 `pstaTextAttr`  
 [in, out] 문자 특성 버퍼입니다. 이 매개 변수가 `NULL` 경우이 메서드는 특성을 반환 하지 않습니다.  
  
 `pcNumChars`  
 [in, out] 반환 된 문자/특성의 실제 수를 나타냅니다. 이 메서드를 호출 하기 전에이 매개 변수를 0으로 설정 해야 합니다.  
  
 `cMaxChars`  
 진행 반환할 최대 문자 수입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_NOTIMPL`|메서드가 구현 되지 않았습니다.|  
  
## <a name="remarks"></a>주의  
 호스트가 `IDebugDocumentHelper::AddDeferredText`를 호출 하지 않는 경우이 메서드는 `E_NOTIMPL`를 반환할 수 있습니다.  
  
> [!NOTE]
> 이 메서드는 원본 문서에서 텍스트를 반환 합니다. 호스트는 문서에 대 한 편집 내용이 나 기타 변경 내용을 추적 하지 않습니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentHost 인터페이스](../../winscript/reference/idebugdocumenthost-interface.md)    
 [IDebugDocumentHelper:: AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)    
 [SOURCE_TEXT_ATTR 열거형](../../winscript/reference/source-text-attr-enumeration.md)