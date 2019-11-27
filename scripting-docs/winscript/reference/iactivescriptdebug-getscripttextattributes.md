---
title: 'IActiveScriptDebug:: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57bd466965f6431a1418df1aa56cf6a7bbbc78cc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576927"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
스크립트 텍스트의 임의 블록에 대 한 텍스트 특성을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrCode`  
 진행 스크립트 블록 텍스트입니다. 이 문자열은 null로 종료할 필요가 없습니다.  
  
 `uNumCodeChars`  
 진행 스크립트 블록 텍스트의 문자 수입니다.  
  
 `pstrDelimiter`  
 진행 스크립트 블록 끝 구분 기호의 주소입니다. 텍스트 스트림에서 `pstrCode` 구문 분석 되는 경우 호스트는 일반적으로 두 개의 작은따옴표 (' ')와 같은 구분 기호를 사용 하 여 스크립트 블록의 끝을 검색 합니다. 이 매개 변수는 호스트에서 사용 하는 구분 기호를 지정 하 여 스크립팅 엔진에서 일부 조건부 기본 전처리를 제공할 수 있도록 합니다. 예를 들어 작은따옴표 [']를 구분 기호로 사용 하기 위한 두 개의 작은따옴표로 바꿉니다. 스크립팅 엔진에서이 정보를 사용 하는 방법 (및)은 스크립팅 엔진에 따라 달라 집니다. 호스트에서 구분 기호를 사용 하 여 스크립트 블록의 끝을 표시 하지 않은 경우이 매개 변수를 NULL로 설정 합니다.  
  
 `dwFlags`  
 진행 스크립트 블록과 연결 된 플래그입니다. 는 다음과 같은 값을 조합 하 여 사용할 수 있습니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|식별자와 점 연산자가 각각 SOURCETEXT_ATTR_IDENTIFIER 및 SOURCETEXT_ATTR_MEMBERLOOKUP 플래그로 식별 되어야 함을 나타냅니다.|  
|GETATTRFLAG_THIS|0x0100|현재 개체의 식별자가 SOURCETEXT_ATTR_THIS 플래그로 식별 되어야 함을 나타냅니다.|  
|GETATTRFLAG_HUMANTEXT|0x8000|SOURCETEXT_ATTR_HUMANTEXT 플래그를 사용 하 여 문자열 내용과 주석 텍스트를 식별 함을 나타냅니다.|  
  
 `pattr`  
 [in, out] 반환 된 특성을 포함 하는 버퍼입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 `IDebugDocumentText` 인터페이스를 구현 하는 스마트 호스트는이 메서드를 사용 하 여 호출을 `IDebugDocumentText::GetText` 메서드에 위임할 수 있습니다.  
  
 스크립트 블록에 대 한이 메서드 스크립틀릿에 대 한 `GetScriptletTextAttributes` 메서드입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptDebug 인터페이스](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [Idebugdocumenttext 인터페이스](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR 열거형](../../winscript/reference/source-text-attr-enumeration.md)