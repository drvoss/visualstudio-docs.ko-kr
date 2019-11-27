---
title: 'IActiveScriptDebug:: EnumCodeContextsOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.EnumCodeContextsOfPosition
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::EnumCodeContextsOfPosition
ms.assetid: 19f44420-bcc8-4c10-8c38-378d96044117
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aedfe5d40d8f4086e30f3a62c070b8ccd5ef2388
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572775"
---
# <a name="iactivescriptdebugenumcodecontextsofposition"></a>IActiveScriptDebug::EnumCodeContextsOfPosition
스마트 호스트에서 `IDebugDocumentContext::EnumCodeContexts` 메서드를 위임 하는 데 사용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT EnumCodeContextsOfPosition(  
   DWORD_PTR                 dwSourceContext,  
   ULONG                     uCharacterOffset,  
   ULONG                     uNumChars,  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwSourceContext`  
 진행 `IActiveScriptParse::ParseScriptText` 또는 `IActiveScriptParse::AddScriptlet`에 제공 되는 소스 컨텍스트입니다.  
  
 `uCharacterOffset`  
 진행 스크립트 텍스트의 시작을 기준으로 하는 문자 오프셋입니다.  
  
 `uNumChars`  
 진행 이 컨텍스트의 문자 수입니다.  
  
 `ppescc`  
 제한이 지정 된 범위에 있는 코드 컨텍스트의 열거자입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 스마트 호스트는이 메서드를 사용 하 여 `IDebugDocumentContext::EnumCodeContexts` 메서드를 위임 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptDebug 인터페이스](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)