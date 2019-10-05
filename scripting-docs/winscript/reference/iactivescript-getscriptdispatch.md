---
title: 'Iactivescript:: Getscriptdispatch | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c329a4dbf42461369441b86f6d9ba18992916366
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935602"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
검색 된 `IDispatch` 메서드 및 현재 실행 중인 스크립트에 연결 된 속성에 대 한 인터페이스입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrItemName`  
 [in] 호출자에 게 연결된 디스패치 개체를 해야 하는 항목의 이름을 포함 하는 버퍼의 주소입니다. 이 매개 변수가 `NULL`, 디스패치 개체를 스크립트에 의해 정의 된 모든 전역 메서드 및 속성의 구성원으로 포함 합니다. 통해 합니다 `IDispatch` 인터페이스와 연결 된 `ITypeInfo` 인터페이스를 호스트에서 보거나 스크립트 메서드를 호출 하 고 스크립트 변수를 수정할 수 있습니다.  
  
 `ppdisp`  
 [out] 스크립트의 전역 메서드 및 속성을 사용 하 여 연결 된 개체에 대 한 포인터를 받는 변수의 주소입니다. 스크립팅 엔진에서 이러한 개체를 지원 하지 않으면 `NULL` 반환 됩니다.  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진에 아직 로드 되지 않았거나 초기화).|  
|`S_FALSE`|스크립팅 엔진을 디스패치 개체를 지원 하지 않습니다. `ppdisp` 매개 변수는 NULL로 설정 됩니다.|  
  
## <a name="remarks"></a>설명  
 속성과 메서드를 호출 하 여 추가할 수 있으므로 합니다 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) 인터페이스는 `IDispatch` 이 메서드에서 반환 된 인터페이스는 새 메서드 및 속성에 동적으로 지원할 수 있습니다. 마찬가지로, 합니다 `IDispatch::GetTypeInfo` 메서드는 반환 해야 새, 고유 `ITypeInfo` 메서드 및 속성에 추가 되 면 인터페이스입니다. 단, 언어 엔진을 변경 하지 말아야 합니다 `IDispatch` 인터페이스를 사용 하 여 호환 되는 방식으로 이전 `ITypeInfo` 반환 하는 인터페이스입니다. 즉, 예를 들어, Dispid 재사용 되지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScript](../../winscript/reference/iactivescript.md)