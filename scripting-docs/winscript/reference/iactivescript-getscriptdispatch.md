---
title: 'IActiveScript:: GetScriptDispatch | Microsoft Docs'
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
ms.openlocfilehash: ba53f2eccde18bd5b2d9c609ea680b50cb7261c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575755"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
현재 실행 중인 스크립트와 연결 된 메서드 및 속성에 대 한 `IDispatch` 인터페이스를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrItemName`  
 진행 호출자가 연결 된 디스패치 개체를 필요로 하는 항목의 이름을 포함 하는 버퍼의 주소입니다. 이 매개 변수를 `NULL` 하는 경우 디스패치 개체는 스크립트에 의해 정의 된 모든 전역 메서드 및 속성의 멤버로를 포함 합니다. 호스트는 `IDispatch` 인터페이스와 연결 된 `ITypeInfo` 인터페이스를 통해 스크립트 메서드를 호출 하거나 스크립트 변수를 확인 하 고 수정할 수 있습니다.  
  
 `ppdisp`  
 제한이 스크립트의 전역 메서드 및 속성과 연결 된 개체에 대 한 포인터를 받는 변수의 주소입니다. 스크립팅 엔진에서 이러한 개체를 지원 하지 않는 경우 `NULL` 반환 됩니다.  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_POINTER`|잘못 된 포인터가 지정 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다. 예를 들어 스크립팅 엔진이 아직 로드 되거나 초기화 되지 않았습니다.|  
|`S_FALSE`|스크립팅 엔진은 디스패치 개체를 지원 하지 않습니다. `ppdisp` 매개 변수는 NULL로 설정 됩니다.|  
  
## <a name="remarks"></a>주의  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) 인터페이스를 호출 하 여 메서드 및 속성을 추가할 수 있으므로이 메서드에서 반환 하는 `IDispatch` 인터페이스는 새 메서드 및 속성을 동적으로 지원할 수 있습니다. 마찬가지로, 메서드 및 속성이 추가 될 때 `IDispatch::GetTypeInfo` 메서드는 고유한 `ITypeInfo` 인터페이스를 새로 반환 해야 합니다. 그러나 해당 언어 엔진은 반환 된 이전 `ITypeInfo` 인터페이스와 호환 되지 않는 방식으로 `IDispatch` 인터페이스를 변경 하면 안 됩니다. 이는 예를 들어 Dispid를 다시 사용 하지 않는 것을 의미 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScript](../../winscript/reference/iactivescript.md)