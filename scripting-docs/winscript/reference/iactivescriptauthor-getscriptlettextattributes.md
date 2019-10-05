---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8f1b5aac6df8d8659fa323f3f1efcb7721d97f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955061"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
scriptlet 텍스트 특성을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszCode`  
 [에 size_is (`cch`)] 확인할 scriptlet 텍스트입니다. 이 문자열 종료 null이 될 필요가 없습니다.  
  
 `cch`  
 [in] 에 사용 되는 크기는 `pszCode` 고 `pattr` 매개 변수입니다.  
  
 `pszDelimiter`  
 [in] 주소 scriptlet의 끝 구분 기호입니다. 때 `pszCode` 구문 분석은 텍스트의 스트림에서 호스트 일반적으로 사용 하 여 (예: 두 개의 작은따옴표), 구분 기호 scriptlet의 끝을 검색 합니다. 구분 기호가 없습니다 scriptlet의 끝을 식별 하는 경우이 매개 변수를 NULL로 설정 합니다.  
  
 `dwFlags`  
 [in] Scriptlet 텍스트 특성을 사용 하 여 연관 된 플래그입니다. 다음 값의 조합일 수 있습니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|SOURCETEXT_ATTR_IDENTIFIER 특성이 있는 식별자를 식별 하 고 SOURCETEXT_ATTR_MEMBERLOOKUP 특성이 있는 점 연산자를 식별 합니다.|  
|GETATTRFLAG_THIS|0x0100|SOURCETEXT_ATTR_THIS 특성이 있는 현재 개체를 식별 합니다.|  
|GETATTRFLAG_HUMANTEXT|0x8000|SOURCETEXT_ATTR_HUMANTEXT 특성을 갖는 문자열 콘텐츠와 주석 텍스트를 식별 합니다.|  
  
 `pattr`  
 [out에서는 size_is (`cch`)] scriptlet 코드에 대 한 색 정보입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR 열거형](../../winscript/reference/source-text-attr-enumeration.md)