---
title: IActiveScriptProperty::GetProperty | Microsoft Docs
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
ms.openlocfilehash: e10d72e289fc2dc31464ce4505cea5c03e8d7f9d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992788"
---
# <a name="iactivescriptpropertygetproperty"></a>IActiveScriptProperty::GetProperty
매개 변수에 의해 지정 된 속성을 가져옵니다.  
  
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
  
 값에 대 한 허용 `dwProperty` 다음 표에 설명 되어 있습니다.  
  
|상수|값|의미|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|스크립팅 엔진에 부동 지점 모드 대신 정수 모드로 나누기를 강제로 수행 합니다.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|교체 스크립팅 엔진의 문자열 비교 함수를 허용 합니다.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|전역 개체에 영향을 주는 다른 스크립팅 엔진이 없습니다 존재 하는 스크립팅 엔진을 알립니다.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|강제로 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진에 지원 되는 데 사용 되는 언어 기능의 집합을 선택 합니다. 지 원하는 언어 기능의 기본 집합을 합니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진은 버전 5.7에서에서 표시 되는 언어 기능 집합에 해당 하는 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진입니다.|  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|명령 실행 성공|  
|`E_INVALIDARG`|인수가 잘못된 경우|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다 (예를 들어, 스크립팅 엔진에 아직 로드 되지 않았거나 초기화).|  
  
## <a name="remarks"></a>설명  
 호스트는 전역 개체에 영향을 주는 다른 스크립팅 엔진이 없습니다 존재 하는 스크립팅 엔진에 알리기 위해 SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION 속성을 사용 수 있습니다. 예를 들어, Internet Explorer를 알릴 수 있습니다 합니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 렌더링할 페이지만 포함 하는 엔진 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립트입니다. 따라서만 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 엔진 전역 개체 창에 새 속성을 추가할 수 있습니다 이며 동일한 작업을 수행 하려면 Visual Basic Scripting Edition (VBScript) 엔진이 없습니다. 엔진은이 플래그는 무시 해도 또는 전역 개체에 추가 되는 새 멤버의 관리 작업을 최적화 하는 데 사용할 수 있습니다.  
  
 호스트 되도록 언어 기능의 집합을 선택 하려면 SCRIPTPROP_INVOKEVERSIONING 속성을 사용할 수 되었을 때를 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진이 시작 될 합니다. 이 속성은 1 (SCRIPTLANGUAGEVERSION_5_7)로 설정 하는 경우 사용 가능한 언어 기능은 버전 5.7에에서 나타난 것과 동일 합니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진입니다. 2 (SCRIPTLANGUAGEVERSION_5_8)로 설정 된 경우 사용 가능한 언어 기능은 버전 5.7 버전 5.8에에서 추가 된 기능 외에도 표시 된 것입니다. 기본적으로이 속성 값은 버전 5.7로 표시 된 언어 기능 집합을 호스트에서 다른 기본 동작을 지원 하지 않는 한 (SCRIPTLANGUAGEVERSION_DEFAULT) 0으로 설정 됩니다. 예를 들어 Internet Explorer 8 옵트인 하는 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 5.8 버전에서 지 원하는 언어 기능 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Internet Explorer 8의 문서 모드는 "Internet Explorer 8 표준" 모드가 될 때 기본적으로 스크립팅 엔진입니다.  
  
## <a name="see-also"></a>참고 항목  
 [문서 호환성 정의](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [버전 정보](../../javascript/reference/javascript-version-information.md)