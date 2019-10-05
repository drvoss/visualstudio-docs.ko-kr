---
title: IDebugMethodField::EnumLocals | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumLocals
helpviewer_keywords:
- IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2306bbf0c44a883c584346c3dbb3dd70e9b39175
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68162611"
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

메서드는 선택한 지역 변수에 대 한 열거자를 만듭니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pAddress`  
 [in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 는 컨텍스트 또는 범위의 지역 변수를 선택 하는 디버그 주소를 나타내는 개체입니다.  
  
 `ppLocals`  
 [out] 반환 합니다는 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 지역 목록을 나타내는 개체;이 고, 그렇지 지역 없는 경우 null 값을 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 S_OK를 반환 하거나 로컬 항목 없음 없으면 S_FALSE를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 지정 된 디버그 주소를 포함 하는 블록 내에 정의 된 변수만 열거 됩니다. 모든 컴파일러에서 생성 된 지역 변수를 포함 하 여 모든 지역에서 필요한 경우 호출 된 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) 메서드.  
  
 메서드는 컨텍스트 또는 블록에 대 한 여러 범위를 포함할 수 있습니다. 예를 들어, 다음 가상된 메서드는 세 가지 범위, 두 개의 내부 블록 및 자체 메서드 본문을 포함합니다.  
  
```csharp  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 합니다 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 개체가 나타내는 `func` 메서드 자체입니다. 호출를 `EnumLocals` 메서드는 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 로 설정 합니다 `Inner Scope 1` 주소 포함 하는 열거형을 반환 합니다.는 `temp1` 예를 들어 변수.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)
