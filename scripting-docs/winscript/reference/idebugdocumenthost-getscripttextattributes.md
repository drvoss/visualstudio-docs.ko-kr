---
title: 'Idebugdocumenthost:: Getscripttextattributes | Microsoft Docs'
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
ms.openlocfilehash: 6a5e56468e51f6d90e37e90c885b6b9df48d5f6e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939237"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
문서 텍스트 블록에 대 한 텍스트 특성을 반환합니다.  
  
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
 [in] 스크립트 블록 텍스트입니다. 이 문자열 종료 null이 될 필요가 없습니다.  
  
 `uNumCodeChars`  
 [in] 스크립트 블록 텍스트의 문자 수입니다.  
  
 `pstrDelimiter`  
 [in] 주소 끝의 스크립트 블록 구분 기호입니다. 때 `pstrCode` 구문 분석은 텍스트의 스트림에서 호스트 일반적으로 사용 하 여 구분 기호를 작은따옴표 두 개 ("), 스크립트 블록의 끝을 검색 하는 등입니다. 이 매개 변수는 일부 조건 기본 전처리를 제공 하 여 스크립팅 엔진의 호스트가 사용한 구분 기호를 지정 합니다 (예를 들어 두 개의 작은따옴표를 구분 기호로 사용 하기 위해 사용 하 여 작은따옴표 ['] 대체). 정확 하 게 하는 방법 (및 여부)은 스크립팅 엔진이 사용 하는 스크립팅 엔진에이 정보에 따라 달라 집니다. 호스트 스크립트 블록의 끝을 표시 하는 구분 기호를 사용 하지 않은 경우이 매개 변수를 NULL로 설정 합니다.  
  
 `dwFlags`  
 [in] 스크립트 블록을 사용 하 여 연결 하는 플래그입니다. 이 값의 조합일 수 있습니다.  
  
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
|`E_NOTIMPL`|호스트는 기본 특성을 사용합니다.|  
  
## <a name="remarks"></a>설명  
 이 메서드는 임의의 텍스트 블록을 문서에 대 한 텍스트 특성을 반환합니다. 반환 하는 호스트에 대해 `E_NOTIMPL`, 기본 특성을 사용 하는 경우.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugDocumentHost 인터페이스](../../winscript/reference/idebugdocumenthost-interface.md)   
 [SOURCE_TEXT_ATTR 열거형](../../winscript/reference/source-text-attr-enumeration.md)