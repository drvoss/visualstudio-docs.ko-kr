---
title: IActiveScriptParse::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptParse.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptParse_AddScriptlet
ms.assetid: 824929f4-4dd3-473a-92d9-0b96acea2f14
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ee5d76060789118e9051c2d8dcc5fc570617f6a8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62954956"
---
# <a name="iactivescriptparseaddscriptlet"></a>IActiveScriptParse::AddScriptlet
스크립트에 코드 scriptlet을 추가 합니다. 호스트 문서를 사용 하 여 스크립트의 영구 상태 밀접 호스트는 스크립트를 복원 하는 일을 담당 하는 환경에서이 메서드는 통하지 않고는 `IPersist*` 인터페이스입니다. 기본 예제는 이벤트에 연결 될 HTML 문서에 포함 된 코드의 스크립틀릿을 허용 하는 HTML 스크립팅 언어 (예를 들어 ONCLICK="button1.text='Exit'").  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddScriptlet(  
    LPCOLESTR pstrDefaultName,       // address of default name of scriptlet  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    LPCOLESTR pstrSubItemName,       // address of subitem name  
    LPCOLESTR pstrEventName,         // address of event name  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // application-defined value for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    BSTR *pbstrName,                 // address of actual name of scriptlet  
    EXCEPINFO *pexcepinfo            // address of exception information  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrDefaultName`  
 [in] Scriptlet과 연결할 기본 이름의 주소입니다. Scriptlet (ONCLICK 위의 예와) 명명 정보가 포함 되지 않는 경우이 이름은 scriptlet을 식별 하려면 사용 됩니다. 이 매개 변수가 `NULL`, 필요한 경우 스크립팅 엔진에서 고유한 이름을 제조 합니다.  
  
 `pstrCode`  
 [in] 추가할 scriptlet 텍스트의 주소입니다. 이 문자열의 해석이 스크립팅 언어에 따라 달라 집니다.  
  
 `pstrItemName`  
 [in] 이 스크립틀릿을 사용 하 여 연결 된 항목 이름을 포함 하는 버퍼의 주소입니다. 외에에서이 매개 변수를 `pstrSubItemName`, scriptlet을 이벤트 처리기 개체를 식별 합니다.  
  
 `pstrSubItemName`  
 [in] 이름을 포함 하는 버퍼의 주소는 `subobject` 의 지정된 된 항목이 있는이 scriptlet 관련이; 명명 된 항목의 형식 정보에서이 이름을 찾을 수 있어야 합니다. Scriptlet 대신 명명 된 항목과 연결 되 면이 매개 변수는 NULL을 `subitem`입니다. 외에에서이 매개 변수를 `pstrItemName`, scriptlet을 이벤트 처리기가 특정 개체를 식별 합니다.  
  
 `pstrEventName`  
 [in] Scriptlet을 이벤트 처리기가 이벤트의 이름을 포함 하는 버퍼의 주소입니다.  
  
 `pstrDelimiter`  
 [in] 주소 scriptlet의 끝 구분 기호입니다. 경우는 `pstrCode` 매개 변수는 텍스트 스트림에서 구문 분석, 2 개의 단일 scriptlet의 끝을 검색 하려면 따옴표 (")와 같은 일반적으로 호스트 구분 기호를 사용 합니다. 이 매개 변수는 일부 조건 기본 전처리를 제공 하 여 스크립팅 엔진의 호스트가 사용한 구분 기호를 지정 합니다 (예를 들어 두 개의 작은따옴표를 구분 기호로 사용 하기 위해 사용 하 여 작은따옴표 ['] 대체). 정확 하 게 하는 방법 (및 여부)는 스크립팅 엔진은 정보의 사용 하 여 스크립팅 엔진에 따라 달라 집니다. 호스트 scriptlet의 끝을 표시 하는 구분 기호를 사용 하지 않은 경우이 매개 변수를 NULL로 설정 합니다.  
  
 `dwSourceContextCookie`  
 [in] 디버깅 목적으로 사용 되는 응용 프로그램 정의 값입니다.  
  
 `ulStartingLineNumber`  
 [in] 시작 됩니다 구문 분석 줄을 지정 하는 0부터 시작 값입니다.  
  
 `dwFlags`  
 [in] Scriptlet과 연결 하는 플래그입니다. 다음 값의 조합일 수 있습니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|SCRIPTTEXT_ISVISIBLE|스크립트 텍스트를 표시 함을 나타냅니다 (따라서 이름으로 호출이 가능) 스크립트의 네임 스페이스에서 전역 변수로 합니다.|  
|SCRIPTTEXT_ISPERSISTENT|스크립팅 엔진이 저장 된 경우이 호출 동안 추가 코드를 저장 해야 있음을 나타냅니다 (호출을 통해 예를 들어 `IPersist*::Save`), 아니면 스크립팅 엔진이 초기화 된 상태로 다시 전환 하 여 다시 설정 됩니다. 이 상태에 대 한 자세한 내용은 스크립트 엔진 상태를 참조 하세요.|  
  
 `pbstrName` ,  
 [out] Scriptlet을 식별 하는 데 사용 하는 실제 이름입니다. 이 기본 설정 순서에는: scriptlet 텍스트의 이름이 명시적으로 지정에 제공 된 기본 이름을 `pstrDefaultName`, 또는 스크립팅 엔진에서 합성 고유 이름입니다.  
  
 `pexcepinfo` ,  
 [out] 예외 정보를 포함 하는 구조체의 주소입니다. DISP_E_EXCEPTION 반환 되 면이 구조체를 채워야 합니다.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`DISP_E_EXCEPTION`|스크립트릿 구문 분석 중에 예외가 발생 했습니다. `pexcepinfo` 매개 변수는 예외에 대 한 정보를 포함 합니다.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_NOTIMPL`|이 메서드가 지원 되지 않습니다. 스크립팅 엔진 스크립틀릿 이벤트 싱크를 추가 하는 것을 지원 하지 않습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진에 아직 로드 되지 않았거나 초기화) 하므로 실패 합니다.|  
|`OLESCRIPT_E_INVALIDNAME`|제공 된 기본 이름을이 스크립팅 언어로 올바르지 않습니다.|  
|`OLESCRIPT_E_SYNTAX`|Scriptlet에 지정 되지 않은 구문 오류가 발생 했습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)