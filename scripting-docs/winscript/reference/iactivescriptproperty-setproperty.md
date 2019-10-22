---
title: 'IActiveScriptProperty:: SetProperty | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptProperty.SetProperty
apilocation:
- scrobj.dll
helpviewer_keywords:
- SetProperty method, IActiveScriptProperty interface
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8307a82f181be20205c7bfcc47e881b0fa1e90
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571313"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
매개 변수로 지정 된 속성을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT SetProperty(  
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
 설정할 속성 값입니다.  
  
 `pvarIndex`  
 사용되지 않습니다.  
  
 `pvarValue`  
 속성 값입니다.  
  
 @No__t_0에 대해 허용 되는 값은 다음 표에 설명 되어 있습니다.  
  
|상수|값|의미|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|스크립팅 엔진이 부동 소수점 모드가 아니라 정수 모드로 분할 되도록 합니다. 기본값은 `False`여야 합니다.|  
|SCRIPTPROP_STRINGCOMPAREINSTANCE|0x00003001|스크립팅 엔진의 string compare 함수를 바꿀 수 있습니다.|  
|SCRIPTPROP_ABBREVIATE_GLOBALNAME_RESOLUTION|0x70000002|전역 개체에 기여할 다른 스크립팅 엔진이 없다는 것을 스크립팅 엔진에 알립니다.|  
|SCRIPTPROP_INVOKEVERSIONING|0x00004000|@No__t_0 스크립팅 엔진에서 지원 되는 언어 기능 집합을 강제로 선택 하도록 합니다. @No__t_0 스크립팅 엔진에서 지 원하는 언어 기능의 기본 집합은 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] scripting engine 버전 5.7에 표시 되는 언어 기능 집합과 동일 합니다.|  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|반환 값|의미|  
|------------------|-------------|  
|`S_OK`|성공할.|  
|`E_INVALIDARG`|인수가 잘못 되었습니다.|  
|`E_UNEXPECTED`|호출이 필요 하지 않습니다. 예를 들어 스크립팅 엔진이 아직 로드 되거나 초기화 되지 않았습니다.|  
  
## <a name="remarks"></a>주의  
 정수 나누기를 사용 하거나 사용 하지 않도록 설정 하려면 `SetProperty`를 호출 하 고 `Boolean`을 `Object`로 변환 합니다. 기본적으로 속성 값은 `False`입니다. @No__t_0로 설정 하는 경우 나누기 연산은 정수만 반환 합니다.  
  
 사용자 지정 문자열 비교를 사용 하거나 사용 하지 않도록 설정 하려면 `SetProperty`를 호출 하 고 `Object` 값을 전달 합니다. 전달 하는 개체는 interface [IActiveScriptStringCompare 인터페이스](../../winscript/reference/iactivescriptstringcompare-interface.md)를 구현 해야 합니다. [IActiveScriptStringCompare 인터페이스](../../winscript/reference/iactivescriptstringcompare-interface.md) 인터페이스의 [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) 메서드는 문자열 비교 함수가 실행 될 때마다 호출 됩니다.  
  
 @No__t_0 스크립팅 엔진이 초기화 될 때 지원 되는 언어 기능 집합을 선택 하려면 `SetProperty`를 호출 하 고 SCRIPTPROP_INVOKEVERSIONING에 사용할 언어 기능 집합에 해당 하는 값을 전달 합니다. 이 속성을 1 (SCRIPTLANGUAGEVERSION_5_7)로 설정 하면 사용 가능한 언어 기능이 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진 버전 5.7에 나타난 것과 동일 합니다. 2 (SCRIPTLANGUAGEVERSION_5_8)로 설정 된 경우 버전 5.8에 추가 된 새로운 기능 외에 버전 5.7에 표시 된 언어 기능을 사용할 수 있습니다. 기본적으로이 속성은 0 (SCRIPTLANGUAGEVERSION_DEFAULT)으로 설정 되며,이는 호스트가 다른 기본 동작을 지원 하지 않는 한 버전 5.7에 나타난 언어 기능 집합과 동일 합니다. 예를 들어 internet explorer 8은 Internet explorer 8의 기본 문서 모드가 "Internet Explorer 8 표준" 모드일 때 기본적으로 버전 5.8 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진에서 지원 되는 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 언어 기능을 opts 합니다. Internet Explorer 8 문서 모드를 Internet Explorer 7 표준 또는 특수 모드로 전환 하면 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진이 버전 5.7 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] scripting engine에 있던 언어 기능 집합만 지원 하도록 다시 설정 됩니다.  
  
> [!NOTE]
> @No__t_0 스크립팅 엔진을 초기화 하는 경우에만 SCRIPTPROP_INVOKEVERSIONING를 설정 해야 합니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 스크립팅 엔진에서 정수 나누기를 사용 하는 방법과 비교 함수의 오버 로드를 허용 하는 방법을 보여 줍니다.  
  
```c#  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## <a name="see-also"></a>참조  
 [문서 호환성   정의](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))  
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)    
 [버전 정보](../../javascript/reference/javascript-version-information.md)