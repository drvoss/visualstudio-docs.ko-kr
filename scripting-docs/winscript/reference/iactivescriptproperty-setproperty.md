---
title: IActiveScriptProperty::SetProperty | Microsoft Docs
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
ms.openlocfilehash: d689b7b2a252b208ae578f9bfd95ab93777f7cc5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63385964"
---
# <a name="iactivescriptpropertysetproperty"></a>IActiveScriptProperty::SetProperty
매개 변수에 의해 지정 된 속성을 설정 합니다.  
  
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
  
 값에 대 한 허용 `dwProperty` 다음 표에 설명 되어 있습니다.  
  
|상수|값|의미|  
|--------------|-----------|-------------|  
|SCRIPTPROP_INTEGERMODE|0x00003000|스크립팅 엔진에 부동 지점 모드 대신 정수 모드로 나누기를 강제로 수행 합니다. 기본값은 `False`입니다.|  
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
 를 사용 하거나 정수 나누기를 사용 하지 않도록 설정 하려면 호출 `SetProperty` 변환한를 `Boolean` 에 `Object`합니다. 속성 값은 기본적으로 `False`입니다. 설정 하면 `True`, 나누기 연산을 정수를 반환 합니다.  
  
 를 사용 하거나 사용자 지정 문자열 비교를 사용 하지 않도록 설정 하려면 호출 `SetProperty` 전달는 `Object` 값입니다. 개체에 전달 하는 인터페이스를 구현 해야 [IActiveScriptStringCompare 인터페이스](../../winscript/reference/iactivescriptstringcompare-interface.md)합니다. 합니다 [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) 메서드는 [IActiveScriptStringCompare 인터페이스](../../winscript/reference/iactivescriptstringcompare-interface.md) 인터페이스에는 문자열 비교 함수가 실행 될 때마다 호출 됩니다.  
  
 때 지원 되는 데 사용 되는 언어 기능의 집합을 선택 하 여 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진을 초기화, 호출 `SetProperty` SCRIPTPROP_INVOKEVERSIONING에 대 한 사용으로 설정 하는 언어 기능에 해당 하는 값을 전달 합니다. 이 속성은 1 (SCRIPTLANGUAGEVERSION_5_7)로 설정 하는 경우 사용 가능한 언어 기능은 버전 5.7에에서 나타난 것과 동일 합니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진입니다. 2 (SCRIPTLANGUAGEVERSION_5_8)로 설정 된 경우 사용 가능한 언어 기능은 버전 5.7 버전 5.8에에서 추가 된 새 기능 외에도 표시 된 것입니다. 기본적으로이 속성 값은 버전 5.7로 표시 된 언어 기능 집합을 호스트에서 다른 기본 동작을 지원 하지 않는 한 (SCRIPTLANGUAGEVERSION_DEFAULT) 0으로 설정 됩니다. 예를 들어, Internet Explorer 8 옵트인 하는 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 5.8 버전에서 지원 되는 언어 기능 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] Internet Explorer 8의 기본 문서 모드는 "Internet Explorer 8 표준" 모드가 될 때 기본적으로 스크립팅 엔진입니다. Internet Explorer 7 표준 문서 모드 Internet Explorer 8 또는 쿼크 모드 전환 다시 설정 합니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 5.7 버전에 존재 하는 언어 기능 집합만 지원 하기 위해 스크립팅 엔진 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진입니다.  
  
> [!NOTE]
> SCRIPTPROP_INVOKEVERSIONING 경우에만 설정 해야 합니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 스크립팅 엔진을 초기화 하는 중입니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는 정수 나누기를 사용 하 여 스크립팅 엔진이 하는 방법과 비교 함수의 오버 로드를 허용 하는 방법을 보여 줍니다.  
  
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
  
## <a name="see-also"></a>참고 항목  
 [문서 호환성 정의](https://docs.microsoft.com/previous-versions/windows/internet-explorer/ie-developer/compatibility/cc288325(v=vs.85))   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [버전 정보](../../javascript/reference/javascript-version-information.md)