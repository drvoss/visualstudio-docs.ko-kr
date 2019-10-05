---
title: 'Idebugdocumenthost:: Getdeferredtext | Microsoft Docs'
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
ms.openlocfilehash: 3e5800a6de15d2d59208022fa44d3c2f4c931e14
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446576"
---
# <a name="idebugdocumenthostgetdeferredtext"></a>IDebugDocumentHost::GetDeferredText
사용 하 여 추가 된 문자의 범위를 반환 합니다 `IDebugDocumentHelper::AddDeferredText` 원래 호스트 문서의 메서드.  
  
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
 [in] 텍스트의 시작 위치를 나타내는 호스트 정의 쿠키입니다.  
  
 `pcharText`  
 [out에서] 문자 텍스트 버퍼입니다. 이 매개 변수 이면이 메서드가 문자를 반환 하지 않는 `NULL`합니다.  
  
 `pstaTextAttr`  
 [out에서] 문자 특성이 버퍼입니다. 이 매개 변수가이 메서드는 특성을 반환 하지 `NULL`합니다.  
  
 `pcNumChars`  
 [out에서] 반환 된 문자/특성의 실제 수를 나타냅니다. 이 매개 변수는이 메서드를 호출 하기 전에 0으로 설정 되어야 합니다.  
  
 `cMaxChars`  
 [in] 반환할 문자의 최대 수입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_NOTIMPL`|메서드가 구현 되지 않았습니다.|  
  
## <a name="remarks"></a>설명  
 이 메서드가 반환할 수 있습니다 `E_NOTIMPL`호스트를 호출 하지 않는 경우 `IDebugDocumentHelper::AddDeferredText`합니다.  
  
> [!NOTE]
> 이 메서드는 원래 문서에서 텍스트를 반환합니다. 호스트는를 추적 하지 편집 또는 문서에 다른 변경 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugDocumentHost 인터페이스](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE_TEXT_ATTR 열거형](../../winscript/reference/source-text-attr-enumeration.md)