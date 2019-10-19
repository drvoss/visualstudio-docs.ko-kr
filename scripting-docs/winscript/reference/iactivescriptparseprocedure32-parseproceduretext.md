---
title: IActiveScriptParseProcedure32::P arseProcedureText | Microsoft Docs
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
ms.openlocfilehash: 713421a43d24d8ed7060b3ec4dfbf0f1c42e6249
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574890"
---
# <a name="iactivescriptparseprocedure32parseproceduretext"></a>IActiveScriptParseProcedure32::P arseProcedureText
지정 된 코드 프로시저를 구문 분석 하 고 프로시저를 이름 공간에 추가 합니다.  
  
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
 진행 평가할 프로시저 텍스트의 주소입니다. 이 문자열의 해석은 스크립팅 언어에 따라 달라 집니다.  
  
 `pstrFormalParams`  
 진행 프로시저에 대 한 정식 매개 변수 이름의 주소입니다. 매개 변수 이름은 스크립팅 엔진에 대 한 적절 한 구분 기호로 분리 되어야 합니다. 이름은 괄호로 묶어야 합니다.  
  
 `pstrProcedureName`  
 진행 구문 분석할 프로시저 이름의 주소입니다.  
  
 `pstrItemName`  
 진행 프로시저를 평가할 컨텍스트를 제공 하는 항목 이름의 주소입니다. 이 매개 변수를 `NULL` 하면 스크립팅 엔진의 전역 컨텍스트에서 코드가 평가 됩니다.  
  
 `punkContext`  
 진행 컨텍스트 개체의 주소입니다. 이 개체는 디버깅 환경에서 사용 하도록 예약 되어 있습니다. 이러한 컨텍스트는 디버거에서 활성 런타임 컨텍스트를 나타내는 컨텍스트를 제공할 수 있습니다. 이 매개 변수를 `NULL` 하는 경우 엔진은 `pstrItemName`를 사용 하 여 컨텍스트를 식별 합니다.  
  
 `pstrDelimiter`  
 진행 프로시저 끝 구분 기호의 주소입니다. 텍스트 스트림에서 `pstrCode` 구문 분석 되는 경우 호스트는 일반적으로 두 개의 작은따옴표 (' ')와 같은 구분 기호를 사용 하 여 프로시저의 끝을 검색 합니다. 이 매개 변수는 호스트에서 사용 하는 구분 기호를 지정 하 여 스크립팅 엔진에서 일부 조건부 기본 전처리를 제공할 수 있도록 합니다. 예를 들어 작은따옴표 [']를 구분 기호로 사용 하기 위한 두 개의 작은따옴표로 바꿉니다. 스크립팅 엔진에서이 정보를 사용 하는 정확한 방법 (및)은 스크립팅 엔진에 따라 달라 집니다. 호스트에서 구분 기호를 사용 하 여 프로시저의 끝을 표시 하지 않은 경우이 매개 변수를 `NULL` 설정 합니다.  
  
 `dwSourceContextCookie`  
 진행 디버깅 목적으로 사용 되는 응용 프로그램 정의 값입니다.  
  
 `ulStartingLineNumber`  
 진행 구문 분석이 시작 되는 줄을 지정 하는 0부터 시작 하는 값입니다.  
  
 `dwFlags`  
 진행 프로시저와 연결 된 플래그입니다. 는 다음과 같은 값을 조합 하 여 사용할 수 있습니다.  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|@No__t_0의 코드가 프로시저의 반환 값을 나타내는 식 임을 나타냅니다. 기본적으로 코드에는 식, 문 목록 또는 스크립트 언어에 의해 프로시저에서 허용 되는 다른 항목이 포함 될 수 있습니다.|  
|SCRIPTPROC_IMPLICIT_THIS|@No__t_0 포인터가 프로시저의 범위에 포함 됨을 나타냅니다.|  
|SCRIPTPROC_IMPLICIT_PARENTS|@No__t_0 포인터의 부모가 프로시저의 범위에 포함 됨을 나타냅니다.|  
  
 `ppdisp`  
 제한이 스크립트의 전역 메서드 및 속성을 포함 하는 개체에 대 한 포인터의 주소입니다. 스크립팅 엔진에서 이러한 개체를 지원 하지 않는 경우 `NULL` 반환 됩니다.  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_NOTIMPL`|이 메서드는 지원되지 않습니다. 스크립팅 엔진은 프로시저에 대 한 런타임 추가를 이름 공간에 지원 하지 않습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예: 스크립팅 엔진이 초기화 되지 않음 또는 닫힘 상태).|  
|`OLESCRIPT_E_SYNTAX`|프로시저에서 지정 되지 않은 구문 오류가 발생 했습니다.|  
|`S_FALSE`|스크립팅 엔진은 디스패치 개체를 지원 하지 않습니다. `ppdisp` 매개 변수는 `NULL`로 설정 됩니다.|  
  
## <a name="remarks"></a>주의  
 이 호출 중에는 스크립트 코드가 평가 되지 않습니다. 대신 프로시저는 나중에 스크립트에서 호출할 수 있는 스크립트 상태로 컴파일됩니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptParseProcedure32](../../winscript/reference/iactivescriptparseprocedure32.md)