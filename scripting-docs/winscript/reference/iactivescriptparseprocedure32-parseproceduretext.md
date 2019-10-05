---
title: IActiveScriptParseProcedure32::ParseProcedureText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ede37171-2f1e-4467-a358-17bd4a4f1869
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: e772d8276de5528f0aed25278a03725d09edb180
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993399"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::ParseProcedureText
지정 된 코드 프로시저를 구문 분석 하 고 프로시저의 네임 스페이스에 추가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ParseProcedureText(  
    LPCOLESTR pstrCode,              // address of procedure text  
    LPCOLESTR pstrFormalParams,      // address of formal parameter names  
    LPCOLESTR pstrProcedureName,     // address of procedure name  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-procedure delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // procedure flags  
    IDispatch **ppdisp               // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrCode`  
 [in] 평가 하 여 프로시저 텍스트의 주소입니다. 이 문자열의 해석이 스크립팅 언어에 따라 달라 집니다.  
  
 `pstrFormalParams`  
 [in] 프로시저에 대 한 정식 매개 변수 이름의 주소입니다. 매개 변수 이름은 스크립팅 엔진에 대 한 적절 한 구분 기호를 사용 하 여 구분 되어야 합니다. 하지 이름은 괄호로 묶어야 합니다.  
  
 `pstrProcedureName`  
 [in] 구문 분석 될 프로시저 이름의 주소입니다.  
  
 `pstrItemName`  
 [in] 프로시저를 계산할 컨텍스트를 제공 하는 항목 이름의 주소입니다. 이 매개 변수가 `NULL`, 코드가 스크립팅 엔진의 전역 컨텍스트에서 평가 됩니다.  
  
 `punkContext`  
 [in] 컨텍스트 개체의 주소입니다. 이 개체는 이러한 컨텍스트는 활성 런타임 컨텍스트를 나타내는 디버거를 통해 제공 될 수 있습니다 위치 디버깅 환경에서 사용 하기 위해 예약 되어 있습니다. 이 매개 변수가 `NULL`, 엔진 사용 `pstrItemName` 컨텍스트를 식별 합니다.  
  
 `pstrDelimiter`  
 [in] 프로시저의 끝 구분 기호의 주소입니다. 때 `pstrCode` 구문 분석은 텍스트의 스트림에서 호스트 일반적으로 사용 하 여 구분 기호를 작은따옴표 두 개 ("), 프로시저의 끝을 검색 하는 등입니다. 이 매개 변수는 일부 조건 기본 전처리를 제공 하 여 스크립팅 엔진의 호스트가 사용한 구분 기호를 지정 합니다 (예를 들어 두 개의 작은따옴표를 구분 기호로 사용 하기 위해 사용 하 여 작은따옴표 ['] 대체). 정확 하 게 하는 방법 (및 여부)는 스크립팅 엔진은 정보의 사용 하 여 스크립팅 엔진에 따라 달라 집니다. 이 매개 변수를 설정 `NULL` 호스트 프로시저의 끝을 표시 하는 구분 기호를 사용 하지 않은 경우.  
  
 `dwSourceContextCookie`  
 [in] 디버깅 목적으로 사용 되는 응용 프로그램 정의 값입니다.  
  
 `ulStartingLineNumber`  
 [in] 시작 됩니다 구문 분석 줄을 지정 하는 0부터 시작 값입니다.  
  
 `dwFlags`  
 [in] 프로시저에 연결 된 플래그입니다. 이 값의 조합일 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|나타내는 코드 `pstrCode` 프로시저의 반환 값을 나타내는 식입니다. 기본적으로 식, 문 목록 또는 다른 스크립트 언어에서 프로시저에서 허용 하는 아무 것도 코드를 포함할 수 있습니다.|  
|SCRIPTPROC_IMPLICIT_THIS|나타내는 `this` 포인터 프로시저의 범위에 포함 됩니다.|  
|SCRIPTPROC_IMPLICIT_PARENTS|나타내는의 부모는 `this` 포인터 프로시저의 범위에 포함 됩니다.|  
  
 `ppdisp`  
 [out] 스크립트의 전역 메서드 및 속성을 포함 하는 개체에 대 한 포인터의 주소입니다. 스크립팅 엔진에서 이러한 개체를 지원 하지 않으면 `NULL` 반환 됩니다.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_NOTIMPL`|이 메서드는 지원되지 않습니다. 스크립팅 엔진에서 프로시저의 네임 스페이스를 런타임에 추가 지원 하지 않습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진은 초기화 되지 않은 또는 닫힘 상태).|  
|`OLESCRIPT_E_SYNTAX`|프로시저에 지정 되지 않은 구문 오류가 발생 했습니다.|  
|`S_FALSE`|스크립팅 엔진을 디스패치 개체를 지원 하지 않습니다. 합니다 `ppdisp` 매개 변수는 설정 `NULL`합니다.|  
  
## <a name="remarks"></a>설명  
 스크립트 코드 없이이 호출 중에 평가 됩니다. 대신 프로시저를 호출할 수 있습니다 스크립트에서 나중에 스크립트 상태로 컴파일됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)