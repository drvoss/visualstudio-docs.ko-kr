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
ms.openlocfilehash: 116cbc7fac0d53b55c9766945d56ecebd27b6785
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577443"
---
# <a name="iactivescriptparseprocedureoldparseproceduretext"></a>IActiveScriptParseProcedureOld::ParseProcedureText
지정 된 코드 프로시저를 구문 분석 하 고 이름 공간에 익명 프로시저를 추가 합니다.  
  
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
 진행 평가할 프로시저 텍스트입니다. 이 문자열의 해석은 스크립팅 언어에 따라 달라 집니다.  
  
 `pstrFormalParams`  
 진행 프로시저에 대 한 정식 매개 변수 이름입니다. 매개 변수 이름은 스크립팅 엔진에 대 한 적절 한 구분 기호로 분리 되어야 합니다. 이름은 괄호로 묶어야 합니다.  
  
 `pstrItemName`  
 진행 프로시저를 평가할 컨텍스트를 제공 하는 명명 된 항목의 이름입니다. 이 매개 변수를 `NULL`하면 스크립팅 엔진의 전역 컨텍스트에서 코드가 평가 됩니다.  
  
 `punkContext`  
 진행 Context 개체입니다. 이 개체는 디버깅 환경에서 사용 하도록 예약 되어 있습니다. 이러한 컨텍스트는 디버거에서 활성 런타임 컨텍스트를 나타내는 컨텍스트를 제공할 수 있습니다. 이 매개 변수를 `NULL`하는 경우 엔진은 `pstrItemName`를 사용 하 여 컨텍스트를 식별 합니다.  
  
 `pstrDelimiter`  
 진행 프로시저의 끝 구분 기호입니다. 텍스트 스트림에서 `pstrCode` 구문 분석 되는 경우 호스트는 일반적으로 두 개의 작은따옴표 (' ')와 같은 구분 기호를 사용 하 여 프로시저의 끝을 검색 합니다. 이 매개 변수는 호스트에서 사용 하는 구분 기호를 지정 하 여 스크립팅 엔진에서 일부 조건부 기본 전처리를 제공할 수 있도록 합니다. 예를 들어 구분 기호로 사용할 작은따옴표 (' ')를 두 개의 작은따옴표로 바꿉니다. 스크립팅 엔진에서이 정보를 사용 하는 방법 (및)은 스크립팅 엔진에 따라 달라 집니다. 호스트에서 구분 기호를 사용 하 여 프로시저의 끝을 표시 하지 않은 경우이 매개 변수를 `NULL` 설정 합니다.  
  
 `dwSourceContextCookie`  
 진행 디버깅 목적으로 사용 되는 응용 프로그램 정의 값입니다.  
  
 `ulStartingLineNumber`  
 진행 구문 분석이 시작 되는 줄을 지정 하는 0부터 시작 하는 값입니다.  
  
 `dwFlags`  
 진행 프로시저와 연결 된 플래그입니다. 는 이러한 값을 조합 하 여 사용할 수 있습니다.  
  
|상수|값|의미|  
|--------------|-----------|-------------|  
|SCRIPTPROC_ISEXPRESSION|0x00000020|`pstrCode`의 코드가 프로시저의 반환 값을 나타내는 식 임을 나타냅니다.|  
|SCRIPTPROC_IMPLICIT_THIS|0x00000100|`this` 포인터가 프로시저의 범위에 포함 됨을 나타냅니다.|  
|SCRIPTPROC_IMPLICIT_PARENTS|0x00000200|`this` 포인터의 부모가 프로시저의 범위에 포함 됨을 나타냅니다.|  
  
 `ppdisp`  
 제한이 기본 메서드가이 메서드에 의해 구문 분석 되는 프로시저인 디스패치 래퍼를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_NOTIMPL`|이 메서드는 지원되지 않습니다. 스크립팅 엔진은 프로시저에 대 한 런타임 추가를 이름 공간에 지원 하지 않습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예: 스크립팅 엔진이 초기화 되지 않음 또는 닫힘 상태).|  
|`OLESCRIPT_E_SYNTAX`|프로시저에서 지정 되지 않은 구문 오류가 발생 했습니다.|  
|`S_FALSE`|스크립팅 엔진은 디스패치 개체를 지원 하지 않습니다. `ppdisp`매개 변수는 `NULL`로 설정 됩니다.|  
  
## <a name="remarks"></a>주의  
 이 호출 중에는 스크립트 코드가 평가 되지 않습니다. 이 프로시저는 나중에 스크립트에서 호출할 수 있는 `ppdisp`에 대 한 메서드로 컴파일됩니다.  
  
 이 인터페이스는 `IActiveScriptParseProcedure` 인터페이스를 위해 더 이상 사용 되지 않습니다. `IActiveScriptParseProcedure::ParseProcedureText` 메서드는이 메서드와 유사 하지만 프로시저 이름을 지정할 수 있습니다. 모든 상황에서 `IActiveScriptParseProcedure::ParseProcedureText`를 사용 해야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptParseProcedureOld 인터페이스](../../winscript/reference/iactivescriptparseprocedureold-interface.md)   
 [IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)