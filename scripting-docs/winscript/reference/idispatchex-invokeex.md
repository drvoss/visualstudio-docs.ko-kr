---
title: 'IDispatchEx:: InvokeEx | Microsoft Docs'
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
ms.openlocfilehash: 8a15acb3211c0d3dd19c0d262efb6cbd3327ab9a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575310"
---
# <a name="idispatchexinvokeex"></a>IDispatchEx::InvokeEx
`IDispatchEx` 개체에서 노출 하는 속성 및 메서드에 대 한 액세스를 제공 합니다.  
  
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
 멤버를 식별합니다. `GetDispID` 또는 `GetNextDispID`를 사용 하 여 디스패치 식별자를 가져옵니다.  
  
 `lcid`  
 인수를 해석할 로캘 컨텍스트입니다. `lcid`은 개체가 로캘과 관련 된 인수를 해석할 수 있도록 `InvokeEx`에 전달 됩니다.  
  
 `wFlags`  
 `wFlags`에 대 한 올바른 값은 다음과 같습니다.  
  
 DISPATCH_PROPERTYGET &#124; DISPATCH_METHOD &#124; DISPATCH_PROPERTYPUT &#124; DISPATCH_PROPERTYPUTREF &#124; DISPATCH_CONSTRUCT  
  
 `InvokeEx` 호출의 컨텍스트를 설명 하는 플래그입니다.  
  
|값|의미|  
|-----------|-------------|  
|DISPATCH_METHOD|멤버가 메서드로 호출 됩니다. 속성 이름이 같은 경우이 플래그와 DISPATCH_PROPERTYGET 플래그를 모두 설정할 수 있습니다 (`IDispatch`에 정의 됨).|  
|DISPATCH_PROPERTYGET|멤버는 속성 또는 데이터 멤버로 검색 됩니다 (`IDispatch`에 의해 정의 됨).|  
|DISPATCH_PROPERTYPUT|멤버는 `IDispatch`에 의해 정의 된 속성 또는 데이터 멤버로 변경 됩니다.|  
|DISPATCH_PROPERTYPUTREF|멤버는 값 할당 대신 참조 할당을 통해 변경 됩니다. 이 플래그는 속성이 `IDispatch`에서 정의한 개체에 대 한 참조를 허용 하는 경우에만 유효 합니다.|  
|DISPATCH_CONSTRUCT|멤버가 생성자로 사용 되 고 있습니다. `IDispatchEx`에서 정의한 새 값입니다. `wFlags`에 대 한 올바른 값은 다음과 같습니다.<br /><br /> DISPATCH_PROPERTYGET DISPATCH_METHOD DISPATCH_PROPERTYPUT DISPATCH_PROPERTYPUTREF DISPATCH_CONSTRUCT|  
  
 `pdp`  
 인수의 배열, 명명된 인수에 대한 인수 DISPID의 배열 및 배열에 있는 요소의 개수가 포함된 구조체에 대한 포인터입니다. DISPPARAMS 구조체에 대 한 전체 설명은 `IDispatch` 설명서를 참조 하세요.  
  
 `pVarRes`  
 결과를 저장할 위치에 대 한 포인터 이거나, 호출자가 결과를 기대 하지 않는 경우 Null입니다. DISPATCH_PROPERTYPUT 또는 DISPATCH_PROPERTYPUTREF 지정 된 경우이 인수는 무시 됩니다.  
  
 `pei`  
 예외 정보가 포함된 구조체에 대한 포인터입니다. `DISP_E_EXCEPTION` 반환 되는 경우이 구조는 채워야 합니다. Null 일 수 있습니다. `EXCEPINFO` 구조에 대 한 전체 설명은 `IDispatch` 설명서를 참조 하세요.  
  
 `pspCaller`  
 호출자가 제공한 서비스 공급자 개체에 대 한 포인터로, 개체가 호출자의 서비스를 가져올 수 있도록 합니다. Null 일 수 있습니다.  
  
 `IDispatchEx::InvokeEx`는 `IDispatch::Invoke`와 동일한 모든 기능을 제공 하 고 몇 가지 확장을 추가 합니다.  
  
|||  
|-|-|  
|DISPATCH_CONSTRUCT|항목이 생성자로 사용 되 고 있음을 나타냅니다.|  
|`pspCaller`|`pspCaller`는 호출자가 제공 하는 서비스에 대 한 개체 액세스를 허용 합니다. 특정 서비스는 호출자 자체에서 처리 되거나 호출 체인을 통해 호출자에 게 위임할 수 있습니다. 예를 들어 브라우저 내의 스크립트 엔진이 외부 개체에 대 한 `InvokeEx` 호출 하는 경우 개체는 `pspCaller` 체인을 따라 스크립트 엔진이 나 브라우저에서 서비스를 가져올 수 있습니다. 호출 체인은 컨테이너 체인이 나 사이트 체인이 라고도 하는 생성 체인과는 다릅니다. 만들기 체인은 `IObjectWithSite`같은 다른 메커니즘을 통해 사용할 수 있습니다.|  
|`this` 포인터|`wFlags`에서 DISPATCH_METHOD 설정 된 경우 "this" 값에 대 한 "명명 된 매개 변수"가 있을 수 있습니다. DISPID는 DISPID_THIS 되며 명명 된 첫 번째 매개 변수 여야 합니다.|  
  
 `IDispatch::Invoke`에서 사용 되지 않은 `riid` 매개 변수가 제거 되었습니다.  
  
 `IDispatch::Invoke`의 `puArgArr` 매개 변수가 제거 되었습니다.  
  
 다음 예제는 `IDispatch::Invoke` 설명서를 참조 하세요.  
  
 "인수 없이 메서드 호출"  
  
 "속성 가져오기 및 설정"  
  
 "매개 변수 전달"  
  
 "인덱싱된 속성"  
  
 "호출 하는 동안 예외 발생"  
  
 "오류 반환"  
  
## <a name="return-value"></a>반환 값  
 는 다음 값 중 하나를 반환 합니다.  
  
|||  
|-|-|  
|`S_OK`|명령 실행 성공|  
|DISP_E_BADPARAMCOUNT|DISPPARAMS에 제공 되는 요소 수는 메서드 또는 속성에서 허용 하는 인수 수와 다릅니다.|  
|DISP_E_BADVARTYPE|`rgvarg`의 인수 중 하나가 올바른 variant 형식이 아닙니다.|  
|DISP_E_EXCEPTION|응용 프로그램에서 예외를 발생 시켜야 합니다. 이 경우 `pei` 전달 된 구조체를 채워야 합니다.|  
|DISP_E_MEMBERNOTFOUND|요청 된 멤버가 없거나 `InvokeEx`에 대 한 호출에서 읽기 전용 속성의 값을 설정 하려고 한 경우|  
|DISP_E_NONAMEDARGS|이 `IDispatch` 구현에서는 명명 된 인수를 지원 하지 않습니다.|  
|DISP_E_OVERFLOW|`rgvarg`의 인수 중 하나를 지정 된 형식으로 강제 변환할 수 없습니다.|  
|DISP_E_PARAMNOTFOUND|매개 변수 Dispid 중 하나가 메서드의 매개 변수와 일치 하지 않는 경우|  
|DISP_E_TYPEMISMATCH|하나 이상의 인수를 강제 변환할 수 없습니다.|  
|DISP_E_UNKNOWNLCID|호출 되는 멤버는 LCID에 따라 문자열 인수를 해석 하며, LCID는 인식 되지 않습니다. LCID가 인수를 해석할 필요가 없으면이 오류가 반환 되지 않습니다.|  
|DISP_E_PARAMNOTOPTIONAL|필수 매개 변수를 생략 했습니다.|  
  
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