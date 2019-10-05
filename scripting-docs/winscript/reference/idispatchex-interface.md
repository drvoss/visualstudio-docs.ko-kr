---
title: IDispatchEx 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispatchEx interface, about IDispatchEx
- IDispatchEx interface
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df3fd7d46fdcb1f3e86bddd53700d7bce6e21381
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000843"
---
# <a name="idispatchex-interface"></a>IDispatchEx 인터페이스
`IDispatchEx`의 확장을 `IDispatch` 인터페이스 스크립팅 언어와 같은 동적 언어에 적합 한 기능을 지원 합니다. 이 섹션에서는 설명의 `IDispatchEx` 간의 차이점을 자체 인터페이스 `IDispatch` 및 `IDispatchEx`, 및 확장에 대 한 합니다. 판독기에 익숙한 것으로 예상 `IDispatch` 에 액세스할 수는 `IDispatch` 설명서.  
  
## <a name="remarks"></a>설명  
 `IDispatch` Microsoft Visual Basic에 대 한 기본적으로 개발 되었습니다. 경우 주된 제한 사항은 `IDispatch` 는 정적 개체는 가정 됩니다. 즉, 개체를 런타임에 변경 하지 않는 있으므로 형식 정보 수 완벽 하 게 설명 컴파일 시. Visual Basic Scripting Edition (VBScript)와 같은 스크립팅 언어에서 발견 되는 동적 런타임에 모델 및 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 동적 HTML 필요한 보다 유연한 인터페이스와 같은 개체를 모델링 합니다.  
  
 `IDispatchEx` 모든 서비스를 제공 하기 위해 개발 된 `IDispatch` 와 같은 스크립팅 언어 보다 동적인 바인딩된 언어에 대 한 적절 한 일부 확장 합니다. 추가 기능의 `IDispatchEx` 제공한 것 이외의 `IDispatch` 됩니다.  
  
- 개체 ("expando")에 새 멤버를 추가, 사용 하 여 `GetDispID` 사용 하 여는 `fdexNameEnsure` 플래그.  
  
- 개체의 멤버를 삭제 합니다.-사용 `DeleteMemberByName` 또는 `DeleteMemberByDispID`합니다.  
  
- 대/소문자 구분 디스패치 작업을 사용 하 여 `fdexNameCaseSensitive` 또는 `fdexNameCaseInsensitive`합니다.  
  
- 암시적 이름의 멤버에 대 한 검색-사용 하 여 `fdexNameImplicit`입니다.  
  
- 개체의 Dispid를 열거-사용 하 여 `GetNextDispID`입니다.  
  
- DISPID에서 요소 이름에 매핑된-사용 하 여 `GetMemberName`입니다.  
  
- 개체 멤버의 속성을 가져올-사용 하 여 `GetMemberProperties`입니다.  
  
- 메서드를 호출 `this` 포인터를 사용 하 여 `InvokeEx` DISPATCH_METHOD를 사용 하 여.  
  
- 가져올 개체의 이름 공간 부모 네임 스페이스의 개념을 지 원하는 브라우저 허용-사용 하 여 `GetNameSpaceParent`입니다.  
  
  개체를 지 원하는 `IDispatchEx` 지원할 수도 있습니다 `IDispatch` 이전 버전과 호환성에 대 한 합니다. 지 원하는 개체의 동적 특성 `IDispatchEx` 에 대 한 몇 가지 의미가 `IDispatch` 해당 개체의 인터페이스입니다. 예를 들어 `IDispatch` 다음 가정 합니다.  
  
- 멤버 및 매개 변수 개체의 수명에 대 한 Dispid 상수 상태로 유지 해야 합니다. 따라서 클라이언트 Dispid를 한 번 가져온를 나중에 사용할 캐시 합니다.  
  
  이후 `IDispatchEx` 추가 및 삭제 멤버 집합이 유효한 Dispid 유지 되지 않습니다 상수를 허용 합니다. 그러나 `IDispatchEx` 는 DISPID 및 멤버 이름 간의 매핑을 일정 하 게 유지 해야 합니다. 즉, 구성원을 삭제 합니다.  
  
- Dispid가 동일한 이름 가진 멤버를 만들 때까지 다시 사용할 수 없습니다.  
  
- Dispid가 유효한 상태를 유지 해야 `GetNextDispID`합니다.  
  
- 경우 DISPID를 정상적으로 동의 해야 합니다는 `IDispatch` 또는 `IDispatchEx` 메서드-삭제 된 멤버를 인식 하 고 (일반적으로 DISP_E_MEMBERNOTFOUND 또는 S_FALSE) 적절 한 오류 코드를 반환 해야 합니다.  
  
## <a name="examples"></a>예제  
 이 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 함수 test ()의 코드는 다음을 수행 합니다.  
  
- 호출 하 여 새 개체를 만듭니다는 `Object` 생성자 변수 Obj. 새 개체에 대 한 포인터를 할당 하 고  
  
- 개체의 Elem 라는 새 요소를 만들고 함수 cat에 대 한 포인터를이 요소에 할당 합니다.  
  
- 이 함수를 호출합니다. 메서드를 호출 하므로 `this` Obj. 개체에 대 한 포인터 참조 새 요소를 추가 하는 함수 개체의 모음입니다.  
  
  전체 HTML 코드는 다음과 같습니다.  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 이 같은 웹 페이지에 배치 되는 컨트롤은 브라우저에서 스크립트 엔진에 디스패치 포인터를 얻을 수 있습니다. 그런 다음 컨트롤 함수 test ()를 구현 수 있습니다.:  
  
```html
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 컨트롤에서 코드, 테스트와 동일한 작업을 수행 합니다 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 함수 `test()`합니다. 이러한 디스패치 호출이 실행으로 수행 되는 참고 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 엔진 및 엔진의 상태를 변경 합니다.  
  
- 사용 하 여 cat 함수를 디스패치 포인터 가져옵니다 `GetDispID()`합니다.  
  
- 사용 하 여 개체를 함수에 대 한 디스패치 포인터를 가져옵니다 `GetDispID()`합니다.  
  
- 개체를 사용 하 여 개체 함수를 호출 하 여 생성 `InvokeEx()` 새로 생성 된 개체에 대 한 디스패치 포인터를 가져옵니다.  
  
- Elem, 새 요소를 사용 하 여 개체를 만듭니다 `GetDispID()` 사용 하 여는 `fdexNameEnsure` 플래그입니다.  
  
- 사용 하 여 요소 c a t 디스패치 포인터를 놓습니다 `InvokeEx()`합니다.  
  
- 호출 하 여 메서드로 디스패치에 대 한 포인터로 고양이 호출 `InvokeEx()` 으로 생성 된 개체에 디스패치 포인터에 전달 하는 `this` 포인터입니다.  
  
- Cat 메서드를 만들고 새 요소를 현재 모음 `this` 개체입니다.  
  
- 확인 하는 새 요소가 가로 막대형,에서 만든 생성된 된 개체를 사용 하 여 요소를 통해 열거 하 여 `GetNextDispID()`입니다.  
  
  테스트 컨트롤에 대 한 코드:  
  
```cpp
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## <a name="methods"></a>메서드  
 [IDispatchEx 메서드](../../winscript/reference/idispatchex-methods.md)