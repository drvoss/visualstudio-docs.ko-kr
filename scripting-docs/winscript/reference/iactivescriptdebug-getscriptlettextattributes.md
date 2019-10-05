---
title: IActiveScriptDebug::GetScriptletTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 781282b5c825954ada4fbb35daa2a97b379c3f13
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955044"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
임의의 scriptlet에 대 한 텍스트 특성을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrCode`  
 [in] Scriptlet 텍스트입니다. 이 문자열에 null로 끝나지 않아도 됩니다.  
  
 `uNumCodeChars`  
 [in] 확인할 scriptlet 텍스트의 문자 수입니다.  
  
 `pstrDelimiter`  
 [in] 주소 scriptlet의 끝 구분 기호입니다. 때 `pstrCode` 구문 분석은 텍스트의 스트림에서 호스트 일반적으로 사용 하 여 구분 기호를 작은따옴표 두 개 ("), scriptlet의 끝을 검색 하는 등입니다. 이 매개 변수는 일부 조건 기본 전처리를 제공 하 여 스크립팅 엔진의 호스트가 사용한 구분 기호를 지정 합니다 (예를 들어 두 개의 작은따옴표를 구분 기호로 사용 하기 위해 사용 하 여 작은따옴표 ['] 대체). 정확 하 게 하는 방법 (및 여부)은 스크립팅 엔진이 사용 하는 스크립팅 엔진에이 정보에 따라 달라 집니다. 호스트 scriptlet의 끝을 표시 하는 구분 기호를 사용 하지 않은 경우이 매개 변수를 NULL로 설정 합니다.  
  
 `dwFlags`  
 [in] Scriptlet과 연결 하는 플래그입니다. 이 값의 조합일 수 있습니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|식별자 및 점 연산자를 식별 SOURCETEXT_ATTR_IDENTIFIER 및 SOURCETEXT_ATTR_MEMBERLOOKUP 플래그를 사용 하 여 각각을 나타냅니다.|  
|GETATTRFLAG_THIS|0x0100|현재 개체에 대 한 식별자는 SOURCETEXT_ATTR_THIS 플래그를 사용 하 여 식별 됨을 나타냅니다.|  
|GETATTRFLAG_HUMANTEXT|0x8000|문자열 콘텐츠와 주석 텍스트는 SOURCETEXT_ATTR_HUMANTEXT 플래그로 식별 됨을 나타냅니다.|  
  
 `pattr`  
 [out에서] 반환 된 특성을 포함 하는 버퍼입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 구현 하는 스마트 호스트로 `IDebugDocumentText` 인터페이스에 대 한 호출을 위임 하려면이 메서드를 사용할 수는 `IDebugDocumentText::GetText` 메서드.  
  
 이 호출에는 스크립틀릿 식 이어야 하는 경향이 있습니다 및 스크립트 블록을 다른 구문이 있을 수 있으므로 제공 됩니다. 이 메서드의 구현은 구현에 동일 동일한 구문을 적이 있으면는 `GetScriptTextAttributes` 메서드.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptDebug 인터페이스](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText 인터페이스](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR 열거형](../../winscript/reference/source-text-attr-enumeration.md)