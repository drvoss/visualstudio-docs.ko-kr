---
title: IActiveScriptAuthorProcedure::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthorProcedure.ParseProcedureText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthorProcedure::ParseProcedureText
ms.assetid: cb6c29c5-c749-48d7-a6a8-ccbf0f9119ec
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c513b105a483d0f80510dff9c91fa2c3f09e0523
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955161"
---
# <a name="iactivescriptauthorprocedureparseproceduretext"></a>IActiveScriptAuthorProcedure::ParseProcedureText
코드 프로시저를 구문 분석 엔진을 작성 하는 스크립트에 코드 프로시저의 텍스트를 추가 하 고, 만듭니다는 `IScriptEntry` 코드 프로시저에 해당 하는 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR   pszCode,  
   LPCOLESTR   pszFormalParams,  
   LPCOLESTR   pszProcedureName,  
   LPCOLESTR   pszItemName,  
   LPCOLESTR   pszDelimiter,  
   DWORD       dwCookie,  
   DWORD       dwFlags,  
   IDispatch   *pdispFor  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszCode`  
 [in] 스크립트 텍스트 구문 분석입니다.  
  
 `pszFormalParams`  
 [in] 프로시저에 대 한 정식 매개 변수 이름의 주소입니다. 매개 변수 이름은 스크립트 엔진 제작에 대 한 적절 한 구분 기호로 구분 되어야 합니다. 하지 이름을 괄호로 묶어야 합니다.  
  
 `pszProcedureName`  
 [in] 구문 분석 될 프로시저 이름의 주소입니다.  
  
 `pszItemName`  
 [in] 항목 이름을 포함 하는 버퍼 주소를 사용 하 여 연결 된 `IScriptEntry` 개체입니다.  
  
 `pszDelimiter`  
 [in] 주소 끝의 스크립트 블록 구분 기호입니다. 때 `pszCode` 구문 분석은 텍스트의 스트림에서 호스트 일반적으로 구분 기호가 사용 (예: 두 개의 작은따옴표), 스크립트 블록의 끝을 검색 합니다. 구분 기호가 없음을 스크립트 블록의 끝을 표시 하는 경우이 매개 변수를 NULL로 설정 합니다.  
  
 `dwCookie`  
 [in] 새 연결 된 응용 프로그램 정의 값을 `IScriptEntry` 개체입니다.  
  
 `dwFlags`  
 [in] 사용 되지 않습니다.  
  
 `pdispFor`  
 [in] 사용 되지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 현재 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 엔진이이 메서드를 구현 하지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptAuthorProcedure 인터페이스](../../winscript/reference/iactivescriptauthorprocedure-interface.md)