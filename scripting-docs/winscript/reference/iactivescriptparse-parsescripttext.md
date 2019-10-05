---
title: IActiveScriptParse::ParseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_ParseScriptText
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3396aee8c044ee9b84d7d6256c6ad69a99965170
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954893"
---
# <a name="iactivescriptparseparsescripttext"></a>IActiveScriptParse::ParseScriptText
네임 스페이스에 선언을 추가 하 고 적절 하 게 코드를 평가 주어진된 코드 스크립트릿 구문 분석 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
  
|||  
|-|-|  
|`pstrCode`|[in] 평가 scriptlet 텍스트의 주소입니다. 이 문자열의 해석이 스크립팅 언어에 따라 달라 집니다.|  
|`pstrItemName`|[in] Scriptlet을 평가할 컨텍스트를 제공 하는 항목 이름의 주소입니다. 이 매개 변수가 NULL 인 경우 코드는 스크립팅 엔진의 전역 컨텍스트에서 평가 됩니다.|  
|`punkContext`|[in] 컨텍스트 개체의 주소입니다. 이 개체는 이러한 컨텍스트는 활성 런타임 컨텍스트를 나타내는 디버거를 통해 제공 될 수 있습니다 위치 디버깅 환경에서 사용 하기 위해 예약 되어 있습니다. 이 매개 변수가 NULL 인 경우 엔진은 사용 `pstrItemName` 컨텍스트를 식별 합니다.|  
|`pstrDelimiter`|[in] 주소 scriptlet의 끝 구분 기호입니다. 때 `pstrCode` 구문 분석은 텍스트의 스트림에서 호스트 일반적으로 사용 하 여 구분 기호를 작은따옴표 두 개 ("), scriptlet의 끝을 검색 하는 등입니다. 이 매개 변수는 일부 조건 기본 전처리를 제공 하 여 스크립팅 엔진의 호스트가 사용한 구분 기호를 지정 합니다 (예를 들어 두 개의 작은따옴표를 구분 기호로 사용 하기 위해 사용 하 여 작은따옴표 ['] 대체). 정확 하 게 하는 방법 (및 여부)는 스크립팅 엔진은 정보의 사용 하 여 스크립팅 엔진에 따라 달라 집니다. 이 매개 변수를 설정 `NULL` 호스트 scriptlet의 끝을 표시 하는 구분 기호를 사용 하지 않은 경우.|  
|`dwSourceContextCookie`|[in] 디버깅 목적으로 사용 되는 쿠키입니다.|  
|`ulStartingLineNumber`|[in] 시작 됩니다 구문 분석 줄을 지정 하는 0부터 시작 값입니다.|  
|`dwFlags`|[in] Scriptlet과 연결 하는 플래그입니다. 이 값의 조합일 수 있습니다.|  
  
|값|의미|  
|-----------|-------------|  
|SCRIPTTEXT_ISEXPRESSION|계산 식과 문 사이의 구분 중요 하지만 스크립트 언어에서 구문상 모호한 경우이 플래그는 scriptlet을 문 또는 문 목록이 아니라 식으로 해석 해야 하는 지정 합니다. 기본적으로 문은 scriptlet 텍스트의 구문에서 적합 한를 확인할 수 있는 경우가 아니면 간주 됩니다.|  
|SCRIPTTEXT_ISPERSISTENT|스크립팅 엔진이 저장 된 경우이 호출 동안 추가 코드를 저장 해야 있음을 나타냅니다 (호출을 통해 예를 들어 `IPersist*::Save`), 아니면 스크립팅 엔진이 초기화 된 상태로 다시 전환 하 여 다시 설정 됩니다.|  
|SCRIPTTEXT_ISVISIBLE|스크립트 텍스트를 표시 함을 나타냅니다 (따라서 이름으로 호출이 가능) 스크립트의 네임 스페이스에서 전역 변수로 합니다.|  
  
|||  
|-|-|  
|`pvarResult`|[out] Scriptlet 처리의 결과 받는 버퍼의 주소 또는 `NULL` 호출자가 아무런 결과 예상 하는 경우 (즉, SCRIPTTEXT_ISEXPRESSION 값 하지 설정 됨).|  
|`pexcepinfo`|[out] 예외 정보를 수신 하는 구조체의 주소입니다. 이 구조는 채워집니다 `IActiveScriptParse::ParseScriptText` DISP_E_EXCEPTION을 반환 합니다.|  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`DISP_E_EXCEPTION`|Scriptlet 처리에 예외가 발생 했습니다. `pexcepinfo` 매개 변수는 예외에 대 한 정보를 포함 합니다.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_NOTIMPL`|이 메서드는 지원되지 않습니다. 스크립팅 엔진의 식이나 문에서 런타임 계산을 지원 하지 않습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진 초기화 되지 않은 또는 닫힘 상태 또는 SCRIPTTEXT_ISEXPRESSION 플래그가 설정 된 이며 스크립팅 엔진이 초기화 된 상태에서).|  
|`OLESCRIPT_E_SYNTAX`|Scriptlet에 지정 되지 않은 구문 오류가 발생 했습니다.|  
  
## <a name="remarks"></a>설명  
 스크립팅 엔진이 초기화 됨 상태에 있으면 코드 없이 실제로 평가할이 호출 하는 동안 이러한 코드 대기 되 고 (또는 진행) 스크립팅 엔진 전환 될 때 실행 되는 대신, 시작된 상태입니다. 실행에 초기화 된 상태에서 허용 되지 않습니다 이므로 초기화 됨 상태에서 SCRIPTTEXT_ISEXPRESSION 플래그를 사용 하 여이 메서드를 호출 하면 오류가 발생 합니다.  
  
 스크립트릿은 식, 문 목록 또는 스크립트 언어에서 허용 하는 아무 것도 수 있습니다. 예를 들어이 메서드는 평가 하는 데 html \<스크립트 > 문은 스크립트 상태로 컴파일되기 보다는 HTML 페이지 생성으로 실행할 수 있는 태그입니다.  
  
 이 메서드에 전달 된 코드는 코드의 유효 하 고 완료 일부 여야 합니다. 예를 들어, VBScript에서이 유효 하지 않은 다음와 함께 두 번째로 하위 Function(x)로 한 번이 메서드를 호출 하려면 `End Sub`합니다. 파서는은 서브루틴을 완료 하려면 두 번째 호출을 대기 하지 않아야 하지만 대신 해야 생성 구문 분석 오류가 서브루틴 선언이 시작 했지만 완료 되지 않은 때문에 합니다.  
  
 스크립트 상태에 대 한 자세한 내용은 스크립트 엔진 상태 섹션을 참조 하세요 [Windows 스크립트 엔진](../../winscript/windows-script-engines.md)합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)