---
title: 'IActiveScriptAuthor:: GetScriptletTextAttributes | Microsoft Docs'
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
ms.openlocfilehash: 4cd0090b9ade47ad37acf6d285ec7f072f1ea5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576178"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Scriptlet의 텍스트 특성을 반환 합니다.  
  
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
 [in, size_is (`cch`)] Scriptlet 텍스트입니다. 이 문자열은 null로 종료할 필요가 없습니다.  
  
 `cch`  
 진행 `pszCode` 및 `pattr` 매개 변수에 사용 되는 크기입니다.  
  
 `pszDelimiter`  
 진행 Scriptlet의 끝 구분 기호 주소입니다. 텍스트 스트림에서 `pszCode` 구문 분석 되는 경우 호스트는 일반적으로 구분 기호 (예: 두 개의 작은따옴표)를 사용 하 여 scriptlet의 끝을 검색 합니다. Scriptlet의 끝을 식별 하는 구분 기호를 사용 하지 않는 경우이 매개 변수를 NULL로 설정 합니다.  
  
 `dwFlags`  
 진행 Scriptlet의 텍스트 특성과 연결 된 플래그입니다. 은 다음 값을 조합 하 여 사용할 수 있습니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|SOURCETEXT_ATTR_IDENTIFIER 특성이 있는 식별자를 식별 하 고 SOURCETEXT_ATTR_MEMBERLOOKUP 특성이 있는 점 연산자를 식별 합니다.|  
|GETATTRFLAG_THIS|0x0100|SOURCETEXT_ATTR_THIS 특성이 있는 현재 개체를 식별 합니다.|  
|GETATTRFLAG_HUMANTEXT|0x8000|SOURCETEXT_ATTR_HUMANTEXT 특성이 있는 문자열 내용과 설명 텍스트를 식별 합니다.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] Scriptlet 코드에 대 한 색 정보입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR 열거형](../../winscript/reference/source-text-attr-enumeration.md)