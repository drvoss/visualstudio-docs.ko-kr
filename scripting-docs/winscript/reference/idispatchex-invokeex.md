---
title: IDispatchEx::InvokeEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.InvokeEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- InvokeEx method
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33494836e463c9c2fd74acf7835d7e4630747b0e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000751"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
노출 하는 메서드와 속성에 액세스할 수는 `IDispatchEx` 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `id`  
 멤버를 식별합니다. 사용 하 여 `GetDispID` 또는 `GetNextDispID` 디스패치 식별자를 가져오려고 합니다.  
  
 `lcid`  
 인수를 해석할 로캘 컨텍스트입니다. `lcid` 넘어갑니다 `InvokeEx` 개체 특정 로캘에 해당 인수를 해석할 수 있도록 합니다.  
  
 `wFlags`  
 유효한 값에 대 한 `wFlags` 됩니다.  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 컨텍스트를 설명 하는 플래그를 `InvokeEx` 호출 합니다.  
  
|값|의미|  
|-----------|-------------|  
|DISPATCH_METHOD|멤버 메서드로 호출 됩니다. 모두이 플래그와 DISPATCH_PROPERTYGET 플래그를 설정할 수 있습니다이 속성 이름이 있으면 (정의한 `IDispatch`).|  
|DISPATCH_PROPERTYGET|속성이 나 데이터 멤버로 검색 하는 (정의한 `IDispatch`).|  
|DISPATCH_PROPERTYPUT|속성 또는 데이터 멤버와 멤버를 변경 (정의한 `IDispatch`).|  
|DISPATCH_PROPERTYPUTREF|값 할당 대신 참조 할당 하 여 멤버를 변경 합니다. 이 플래그는 속성은 개체에 대 한 참조를 허용 하는 경우에 유효 (정의한 `IDispatch`).|  
|DISPATCH_CONSTRUCT|멤버는 생성자로 사용 중입니다. (이 정의 되는 새 값 `IDispatchEx`). 유효한 값에 대 한 `wFlags` 됩니다.<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 인수의 배열, 명명된 인수에 대한 인수 DISPID의 배열 및 배열에 있는 요소의 개수가 포함된 구조체에 대한 포인터입니다. 참조 된 `IDispatch` 설명은 DISPPARAMS 구조체에 대 한 설명서입니다.  
  
 `pVarRes`  
 결과 호출자가 아무런 결과 예상 하는 경우에 Null 또는 저장 될 위치에 대 한 포인터입니다. DISPATCH_PROPERTYPUT 또는 DISPATCH_PROPERTYPUTREF를 지정 하는 경우이 인수는 무시 됩니다.  
  
 `pei`  
 예외 정보가 포함된 구조체에 대한 포인터입니다. 경우에이 구조체를 채워야 할 `DISP_E_EXCEPTION` 반환 됩니다. Null 일 수 있습니다. 참조 된 `IDispatch` 에 대 한 전체 설명은 설명서는 `EXCEPINFO` 구조입니다.  
  
 `pspCaller`  
 호출자에서 서비스를 가져올 개체를 허용 하는 호출자가 제공한 서비스 공급자 개체에 대 한 포인터입니다. Null 일 수 있습니다.  
  
 `IDispatchEx::InvokeEx` 모두 동일한 기능을 제공 하므로 `IDispatch::Invoke` 몇 가지 확장을 추가 합니다.  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|항목을 생성자로 사용 되 고 있는지를 나타냅니다.|  
|`pspCaller`|`pspCaller` 호출자가 제공 하는 서비스에 대 한 개체 액세스를 허용 합니다. 특정 서비스 자체는 호출자가 처리 되었거나 호출자를 추가로 호출 체인에 위임 합니다. 예를 들어 경우는 스크립트 엔진 내에서 브라우저를 사용 하면를 `InvokeEx` 외부 개체에 개체 호출 따르면는 `pspCaller` 스크립트 엔진 또는 브라우저에서 서비스를 얻기 위한 체인입니다. (호출 체인은 체인 만들기와 동일-컨테이너 체인 또는 사이트 체인 라고도 합니다. 체인 만들기와 같은 일부 다른 메커니즘을 통해 사용할 수 `IObjectWithSite`.)|  
|`this` 포인터|설정 하면에 DISPATCH_METHOD `wFlags`, "명명된 된 매개 변수" "this"이 값이 있을 수 있습니다. 경우 DISPID DISPID_THIS 되며 명명된 된 첫 번째 매개 변수 여야 합니다.|  
  
 사용 되지 않은 `riid` 매개 변수에서 `IDispatch::Invoke` 제거 되었습니다.  
  
 합니다 `puArgArr` 매개 변수에서 `IDispatch::Invoke` 제거 되었습니다.  
  
 참조 된 `IDispatch::Invoke` 다음 예제에 대 한 설명서:  
  
 "인수를 사용 하 여 메서드를 호출"  
  
 "속성 가져오기 및 설정"  
  
 "매개 변수 전달"  
  
 "인덱싱된 속성"  
  
 "호출 하는 동안 예외 발생"  
  
 "오류를 반환 합니다"  
  
## <a name="return-value"></a>반환 값  
 다음 값 중 하나를 반환합니다.  
  
|||  
|-|-|  
|`S_OK`|명령 실행 성공|  
|DISP_E_BADPARAMCOUNT|DISPPARAMS에 제공 된 요소 수가 메서드 또는 속성에서 허용 하는 인수 개수와 다릅니다.|  
|DISP_E_BADVARTYPE|인수 중 하나가 `rgvarg` 유효한 variant 형식이 아닙니다.|  
|DISP_E_EXCEPTION|응용 프로그램에서 예외가 발생 해야 합니다. 구조에 전달 하는 예제의 경우 `pei` 입력 해야 합니다.|  
|DISP_E_MEMBERNOTFOUND|요청한 멤버가 존재 하지 않는 또는 호출 `InvokeEx` 읽기 전용 속성의 값을 설정 하려고 합니다.|  
|DISP_E_NONAMEDARGS|이 구현의 `IDispatch` 명명 된 인수를 지원 하지 않습니다.|  
|DISP_E_OVERFLOW|인수 중 하나가 `rgvarg` 강제 지정된 된 형식으로 변환 될 수 있습니다.|  
|DISP_E_PARAMNOTFOUND|Dispid 매개 변수 중 하나는 메서드의 매개 변수에 일치 하지 않습니다.|  
|DISP_E_TYPEMISMATCH|하나 이상의 인수를 바꿀 수 없습니다.|  
|DISP_E_UNKNOWNLCID|호출 되는 멤버의 LCID에 따라 문자열 인수를 해석할 LCID 인식 되지 않습니다. LCID 인수를 해석할 필요 하지 않으면이 오류를 반환 되어야 합니다.|  
|DISP_E_PARAMNOTOPTIONAL|필수 매개 변수를 생략 되었습니다.|  
  
## <a name="example"></a>예제  
  
```cpp
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## <a name="see-also"></a>참고 항목  
 [IDispatchEx 인터페이스](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)