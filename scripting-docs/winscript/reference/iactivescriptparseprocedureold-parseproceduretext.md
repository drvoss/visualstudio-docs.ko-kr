---
title: IActiveScriptParseProcedureOld::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParseProcedureOld.ParseProcedureText
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptParseProcedureOld::ParseProcedureText
ms.assetid: 21a21313-35ce-432d-b9a6-7999065f19ac
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e521bbdcd8d7397c1c2dfb377fd9b41811499f5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993217"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
지정 된 코드 프로시저를 구문 분석 하 고 프로시저를 익명 네임 스페이스를 추가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ParseProcedureText(  
   LPCOLESTR    pstrCode,  
   LPCOLESTR    pstrFormalParams,  
   LPCOLESTR    pstrItemName,  
   IUnknown*    punkContext,  
   LPCOLESTR    pstrDelimiter,  
   DWORD_PTR    dwSourceContextCookie,  
   ULONG        ulStartingLineNumber,  
   DWORD        dwFlags,  
   IDispatch**  ppdisp  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrCode`  
 [in] 프로시저의 텍스트는 계산입니다. 이 문자열의 해석이 스크립팅 언어에 따라 달라 집니다.  
  
 `pstrFormalParams`  
 [in] 프로시저에 대 한 정식 매개 변수 이름입니다. 매개 변수 이름은 스크립팅 엔진에 대 한 적절 한 구분 기호를 사용 하 여 구분 되어야 합니다. 하지 이름은 괄호로 묶어야 합니다.  
  
 `pstrItemName`  
 [in] 프로시저를 계산할 컨텍스트를 제공 하는 명명 된 항목의 이름입니다. 이 매개 변수가 `NULL`, 코드가 스크립팅 엔진의 전역 컨텍스트에서 평가 됩니다.  
  
 `punkContext`  
 [in] 컨텍스트 개체입니다. 이 개체는 이러한 컨텍스트는 활성 런타임 컨텍스트를 나타내는 디버거를 통해 제공 될 수 있습니다 위치 디버깅 환경에서 사용 하기 위해 예약 되어 있습니다. 이 매개 변수가 `NULL`, 엔진 사용 `pstrItemName` 컨텍스트를 식별 합니다.  
  
 `pstrDelimiter`  
 [in] 프로시저의 끝 구분 기호입니다. 때 `pstrCode` 구문 분석은 텍스트의 스트림에서 호스트 일반적으로 사용 하 여 구분 기호를 작은따옴표 두 개 ("), 프로시저의 끝을 검색 하는 등입니다. 이 매개 변수는 일부 조건부를 제공 하 여 스크립팅 엔진의 호스트가 사용한 구분 기호를 지정 합니다. 기본 전처리 (예: 두 개의 작은따옴표를 구분 기호로 사용 하기 위해 작은따옴표 ['] 대체). 정확 하 게 하는 방법 (및 여부)은 스크립팅 엔진이 사용 하는 스크립팅 엔진에이 정보에 따라 달라 집니다. 이 매개 변수를 설정 `NULL` 호스트 프로시저의 끝을 표시 하는 구분 기호를 사용 하지 않은 경우.  
  
 `dwSourceContextCookie`  
 [in] 디버깅 목적으로 사용 되는 응용 프로그램 정의 값입니다.  
  
 `ulStartingLineNumber`  
 [in] 지정 된 줄을 구문 분석을 시작할 0부터 시작 값입니다.  
  
 `dwFlags`  
 [in] 프로시저에 연결 된 플래그입니다. 이 값의 조합일 수 있습니다.  
  
|상수|값|의미|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|나타내는 코드 `pstrCode` 프로시저의 반환 값을 나타내는 식입니다.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|나타내는 `this` 포인터 프로시저의 범위에 포함 됩니다.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|나타내는의 부모는 `this` 포인터 프로시저의 범위에 포함 됩니다.|  
  
 `ppdisp`  
 [out] 기본 방법은이 메서드에 의해 구문 분석 하는 절차는 디스패치 래퍼를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_NOTIMPL`|이 메서드는 지원되지 않습니다. 스크립팅 엔진에서 프로시저의 네임 스페이스를 런타임에 추가 지원 하지 않습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진은 초기화 되지 않은 또는 닫힘 상태).|  
|`OLESCRIPT_E_SYNTAX`|프로시저에 지정 되지 않은 구문 오류가 발생 했습니다.|  
|`S_FALSE`|스크립팅 엔진을 디스패치 개체를 지원 하지 않습니다. 합니다 `ppdisp`매개 변수는 설정 `NULL`합니다.|  
  
## <a name="remarks"></a>설명  
 스크립트 코드 없이이 호출 중에 평가 됩니다. 프로시저를 컴파일할 메서드로 대신, `ppdisp` 를 호출할 수 있습니다 스크립트에서 나중에 있습니다.  
  
 위해이 인터페이스는 사용 되지 않습니다는 `IActiveScriptParseProcedure` 인터페이스입니다. `IActiveScriptParseProcedure::ParseProcedureText` 메서드는이 메서드와 비슷하지만 있지만 프로시저 이름을 지정할 수 있습니다. 모든 상황에서 `IActiveScriptParseProcedure::ParseProcedureText` 사용 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptParseProcedureOld 인터페이스](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)