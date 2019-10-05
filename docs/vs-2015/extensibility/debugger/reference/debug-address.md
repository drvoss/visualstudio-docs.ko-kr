---
title: DEBUG_ADDRESS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- DEBUG_ADDRESS
helpviewer_keywords:
- DEBUG_ADDRESS structure
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d001d29433573fedde3b4310f989667538b4b69c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444964"
---
# <a name="debugaddress"></a>DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

이 구조는 주소를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```csharp  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## <a name="terms"></a>용어  
 ulAppDomainID  
 프로세스 id입니다.  
  
 guidModule  
 이 주소를 포함 하는 모듈의 GUID입니다.  
  
 tokClass  
 클래스 또는이 주소의 형식 식별 토큰입니다.  
  
> [!NOTE]
> 이 값은 기호 공급자에 국한 되며 따라서 의미가 없는 일반 이외의 다른 클래스 형식에 대 한 식별자로.  
  
 addr  
 A [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 개별 주소 형식을 설명 하는 구조체의 공용 구조체를 포함 하는 구조입니다. 값 `addr`합니다.`dwKind` 제공 되는 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) 열거형, 공용 구조체를 해석 하는 방법에 설명 합니다.  
  
## <a name="remarks"></a>설명  
 이 구조에 전달 되는 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 메서드를 채울 수 있습니다.  
  
 **경고 [C++ 만]**  
  
 경우 `addr.dwKind` 됩니다 `ADDRESS_KIND_METADATA_LOCAL` 경우에 `addr.addr.addrLocal.pLocal` 호출 해야 합니다는 null 값이 아닙니다 `Release` 토큰 포인터:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [구조체 및 공용 구조체](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
