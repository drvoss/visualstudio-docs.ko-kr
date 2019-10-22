---
title: IDebugExpressionContext::P arseLanguageText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.ParseLanguageText
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::ParseLanguageText
ms.assetid: 650cb016-7d80-4011-b264-780f871a3466
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0493adde76e029088b637be3c6aaf02c55caaace
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573158"
---
# <a name="idebugexpressioncontextparselanguagetext"></a>IDebugExpressionContext::ParseLanguageText
지정 된 텍스트에 대 한 디버그 식을 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT ParseLanguageText(  
   LPCOLESTR           pstrCode,  
   UINT                nRadix,  
   LPCOLESTR           pstrDelimiter,  
   DWORD               dwFlags,  
   IDebugExpression**  ppe  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrCode`  
 진행 식 또는 문의 텍스트를 제공 합니다.  
  
 `nRadix`  
 진행 사용할 기 수입니다.  
  
 `pstrDelimiter`  
 진행 스크립트 블록의 끝 구분 기호입니다. 텍스트 스트림에서 `pstrCode` 구문 분석 되는 경우 호스트는 일반적으로 두 개의 작은따옴표 (' ')와 같은 구분 기호를 사용 하 여 스크립트 블록의 끝을 검색 합니다. 이 매개 변수는 호스트에서 사용 하는 구분 기호를 지정 하 여 스크립팅 엔진에서 일부 조건부 기본 전처리를 제공할 수 있도록 합니다. 예를 들어 작은따옴표 [']를 구분 기호로 사용 하기 위한 두 개의 작은따옴표로 바꿉니다. 스크립팅 엔진에서이 정보를 사용 하는 방법 (및)은 스크립팅 엔진에 따라 달라 집니다. 호스트에서 구분 기호를 사용 하 여 스크립트 블록의 끝을 표시 하지 않은 경우이 매개 변수를 `NULL`으로 설정 합니다.  
  
 `dwFlags`  
 진행 다음 디버그 텍스트 플래그의 조합입니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|DEBUG_TEXT_ISEXPRESSION|0x00000001|문이 문이 아닌 식 임을 나타냅니다. 이 플래그는 일부 언어에서 텍스트를 구문 분석 하는 방법에 영향을 줄 수 있습니다.|  
|DEBUG_TEXT_RETURNVALUE|0x00000002|반환 값을 사용할 수 있는 경우이 값은 호출자가 사용 합니다.|  
|DEBUG_TEXT_NOSIDEEFFECTS|0x00000004|의도 하지 않은 결과를 허용 하지 않습니다. 이 플래그가 설정 된 경우 식의 계산은 런타임 상태를 변경 하지 않아야 합니다.|  
|DEBUG_TEXT_ALLOWBREAKPOINTS|0x00000008|텍스트를 계산 하는 동안 중단점을 허용 합니다. 이 플래그를 설정 하지 않으면 텍스트를 계산 하는 동안 중단점이 무시 됩니다.|  
|DEBUG_TEXT_ALLOWERRORREPORT|0x00000010|텍스트를 평가 하는 동안 오류 보고서를 허용 합니다. 이 플래그를 설정 하지 않으면 평가 중에 호스트에 오류가 보고 되지 않습니다.|  
|DEBUG_TEXT_EVALUATETOCODECONTEXT|0x00000020|식이 식 자체를 실행 하는 대신 코드 컨텍스트로 계산 됨을 나타냅니다.|  
  
 `ppe`  
 제한이 지정 된 텍스트에 대 한 디버그 식을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 지정 된 텍스트에 대 한 디버그 식을 만듭니다.  
  
## <a name="see-also"></a>참조  
 [IDebugExpressionContext 인터페이스](../../winscript/reference/idebugexpressioncontext-interface.md)