---
title: 'IDebugDocumentHost:: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b18f4f49fa157b78e4f1fd6c7766e929890a6c6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569209"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
문서 텍스트 블록의 텍스트 특성을 반환 합니다.  
  
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
|`E_NOTIMPL`|호스트는 기본 특성만 사용 합니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 임의의 문서 텍스트 블록에 대 한 텍스트 특성을 반환 합니다. 호스트는 `E_NOTIMPL`를 반환할 수 있으며,이 경우 기본 특성이 사용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugDocumentHost 인터페이스](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE_TEXT_ATTR 열거형](../../winscript/reference/source-text-attr-enumeration.md)