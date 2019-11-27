---
title: 'IActiveScriptProperty:: GetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.GetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetProperty method, IActiveScriptProperty interface
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1eeec6472a067d18a8b8962cfac70c25c0ff971
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571420"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
매개 변수로 지정 된 속성을 가져옵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:  
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwProperty`  
 가져올 속성 값입니다.  
  
 `pvarIndex`  
 사용되지 않습니다.  
  
 `pvarValue`  
 속성 값입니다.  
  
 `dwProperty`에 대해 허용 되는 값은 다음 표에 설명 되어 있습니다.  
  
|상수|값|의미|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|스크립팅 엔진이 부동 소수점 모드가 아니라 정수 모드로 분할 되도록 합니다.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|스크립팅 엔진의 string compare 함수를 바꿀 수 있습니다.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|전역 개체에 기여할 다른 스크립팅 엔진이 없다는 것을 스크립팅 엔진에 알립니다.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진에서 지원 되는 언어 기능 집합을 강제로 선택 하도록 합니다. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진에서 지 원하는 언어 기능의 기본 집합은 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] scripting engine 버전 5.7에 표시 되는 언어 기능 집합과 동일 합니다.|  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_INVALIDARG`|인수가 잘못된 경우|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다. 예를 들어 스크립팅 엔진이 아직 로드 되거나 초기화 되지 않았습니다.|  
  
## <a name="remarks"></a>주의  
 호스트는 SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION 속성을 사용 하 여 글로벌 개체에 기여할 다른 스크립팅 엔진이 없다는 것을 스크립팅 엔진에 알릴 수 있습니다. 예를 들어 Internet Explorer는 렌더링 되는 페이지에 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립트만 포함 되어 있음을 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 엔진에 알릴 수 있습니다. 따라서 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 엔진 에서만 전역 개체 창에 새 속성을 추가할 수 있으며 동일한 작업을 수행 하는 Visual Basic Scripting Edition (VBScript) 엔진이 없습니다. 엔진은이 플래그를 무시 하거나 전역 개체에 추가 되는 새 멤버의 관리를 최적화 하는 데 사용할 수 있습니다.  
  
 호스트는 SCRIPTPROP_INVOKEVERSIONING 속성을 사용 하 여 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진을 시작할 때 지원 되는 언어 기능 집합을 선택할 수 있습니다. 이 속성을 1 (SCRIPTLANGUAGEVERSION_5_7)로 설정 하면 사용 가능한 언어 기능이 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] scripting engine 버전 5.7에 표시 된 기능과 동일 합니다. 2 (SCRIPTLANGUAGEVERSION_5_8)로 설정 된 경우 버전 5.8에 추가 된 기능 외에 버전 5.7에 표시 된 언어 기능을 사용할 수 있습니다. 기본적으로이 속성은 0 (SCRIPTLANGUAGEVERSION_DEFAULT)으로 설정 되며,이는 호스트가 다른 기본 동작을 지원 하지 않는 한 버전 5.7에 나타난 언어 기능 집합과 동일 합니다. 예를 들어 internet explorer 8은 Internet explorer 8의 문서 모드가 "Internet Explorer 8 표준" 모드일 때 기본적으로 버전 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진에서 지 원하는 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 언어 기능을 opts 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [문서 호환성  정의](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))  
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [버전 정보](../../javascript/reference/javascript-version-information.md)