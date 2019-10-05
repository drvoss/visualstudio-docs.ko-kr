---
title: IDebugProperty3::GetStringChars | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 661cf6833c292d5ff4015649d494ee3a7d04fdbb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419879"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 속성을 사용 하 여 연결 된 문자열을 검색 하 고 사용자가 제공한 버퍼에 저장 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetStringChars(  
   ULONG  buflen,  
   WCHAR* rgString,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetStringChars(  
   uint       buflen,   
   out string rgString,   
   out uint   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `buflen`  
 [in] 최대 문자 수는 사용자가 제공한 버퍼를 포함할 수 있습니다.  
  
 `rgString`  
 [out] 문자열을 반환합니다.  
  
 [C++ 만], `rgString` 문자열의 유니코드 문자를 받는 버퍼에 대 한 포인터입니다. 이 버퍼 이상 이어야 합니다 `buflen` 크기에서 (바이트 아님) 문자입니다.  
  
 `pceltFetched`  
 [out] 여기서 실제로 버퍼에 저장 하는 문자 수가 반환 됩니다. (일 수 있습니다 `NULL` 에서 C++.)  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`; 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 C++, 버퍼 이상 인지 확인 하려면 주의 해야 `buflen` 자의 유니코드 문자입니다. 2 바이트 유니코드 문자는 참고 합니다.  
  
> [!NOTE]
> C++에서 반환된 된 문자열에 null 종결 문자 포함 되지 않습니다. 주어진 경우 `pceltFetched` 문자열의 문자 수를 지정 합니다.  
  
## <a name="example"></a>예제  
<!-- TODO: review snippet reference  [!CODE [[cpp]]([cpp])]  -->  
  
```  
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)  
{  
    CStringW returnString = L"";  
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;  
    If (pProp3 != NULL) {  
        ULONG dwStrLen = 0;  
        HRESULT hr;  
        hr = pProp3->GetStringCharLength(&dwStrLen);  
        if (SUCCEEDED(hr) && dwStrLen > 0) {  
            ULONG dwRead;  
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);  
            hr = pProp3->GetStringChars(dwStrLen,  
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),  
                                        &dwRead);  
        }  
    }  
    return(returnString);  
```  
  
<!-- TODO: review snippet reference  [!CODE [}](})]  -->  
  
## <a name="see-also"></a>참고 항목  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)