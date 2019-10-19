---
title: 'IDebugDocumentHelper:: AddDeferredText | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.AddDeferredText
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::AddDeferredText
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1aae73e44059b1f07fa4cb54f40cdcd12e564a8f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577049"
---
# <a name="idebugdocumenthelperadddeferredtext"></a>IDebugDocumentHelper::AddDeferredText
지정 된 텍스트를 사용할 수 있지만 해당 문자를 제공 하지 않는 도우미에 게 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `cChars`  
 진행 더할 (유니코드) 문자 수입니다.  
  
 `dwTextStartCookie`  
 진행 텍스트의 시작 위치를 나타내는 호스트 정의 쿠키입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_FAIL`|메서드가 실패 했습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드를 사용 하면 호스트에서 필요할 때까지 추가할 문자를 제공 하는 것을 연기 하 고 도우미에서 정확한 알림과 크기 정보를 생성할 수 있습니다. @No__t_0 매개 변수는 호스트에서 정의 되 고 텍스트의 시작 위치를 나타내는 쿠키입니다. @No__t_0에 대 한 후속 호출은이 쿠키를 제공 해야 합니다. 예를 들어 DBCS의 텍스트를 나타내는 호스트에서 쿠키는 바이트 오프셋이 될 수 있습니다.  
  
 @No__t_0에 대 한 단일 호출이 `AddDeferredText`에 대 한 여러 호출에서 문자를 가져올 수 있다고 가정 합니다. 도우미 클래스는 동일한 범위의 지연 문자를 두 번 이상 요청할 수도 있습니다.  
  
> [!NOTE]
> @No__t_0에 대 한 호출은 `AddUnicodeText` 또는 `AddDBCSText`에 대 한 호출과 혼합할 수 없습니다. 이 문제가 발생 하면 `E_FAIL` 반환 됩니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentHelper 인터페이스](../../winscript/reference/idebugdocumenthelper-interface.md)    
 [IDebugDocumentHelper:: AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)    
 [IDebugDocumentHelper:: AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)    
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)