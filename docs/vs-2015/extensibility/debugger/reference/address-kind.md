---
title: ADDRESS_KIND | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- ADDRESS_KIND
helpviewer_keywords:
- ADDRESS_KIND enumeration
ms.assetid: 3a12fbec-7088-4cf9-8f6f-ad8ddec6009a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6152ff5f493134812916f28e0b908bf98ecdbb35
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62561875"
---
# <a name="addresskind"></a>ADDRESS_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

주소의 종류를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
typedef DWORD ADDRESS_KIND;  
```  
  
```csharp  
public enum enum_ADDRESS_KIND {  
   ADDRESS_KIND_NATIVE                  = 0x0001,  
   ADDRESS_KIND_UNMANAGED_THIS_RELATIVE = 0x0002,  
   ADDRESS_KIND_UNMANAGED_PHYSICAL      = 0x0005,  
   ADDRESS_KIND_METADATA_METHOD         = 0x0010,  
   ADDRESS_KIND_METADATA_FIELD          = 0x0011,  
   ADDRESS_KIND_METADATA_LOCAL          = 0x0012,  
   ADDRESS_KIND_METADATA_PARAM          = 0x0013,  
   ADDRESS_KIND_METADATA_ARRAYELEM      = 0x0014,  
   ADDRESS_KIND_METADATA_RETVAL         = 0x0015,  
};  
```  
  
## <a name="terms"></a>용어  
 ADDRESS_KIND_NATIVE  
 기본 주소를 표시 합니다 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) 구조입니다.  
  
 ADDRESS_KIND_UNMANAGED_THIS_RELATIVE  
 기준으로 관리 되지 않는 주소를 `this` (`Me` Visual Basic의) 포인터 나타내는 및 합니다 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) 구조입니다.  
  
 ADDRESS_KIND_UNMANAGED_PHYSICAL  
 나타내는 관리 되지 않는 실제 주소를 합니다 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) 구조입니다.  
  
 ADDRESS_KIND_METHOD  
 나타내는 클래스의 메서드를 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) 구조입니다.  
  
 ADDRESS_KIND_FIELD  
 나타내는 클래스의 필드를 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) 구조입니다.  
  
 ADDRESS_KIND_LOCAL  
 주소를 지역 변수에 대해 이며은 표현 합니다 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) 구조입니다.  
  
 ADDRESS_KIND_PARAM  
 메서드 또는 함수 매개 변수를 표시 합니다 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) 구조입니다.  
  
 ADDRESS_KIND_ARRAYELEM  
 배열 요소를 표시 합니다 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) 구조입니다.  
  
 ADDRESS_KIND_RETVAL  
 반환 값으로 표시 합니다 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) 구조입니다.  
  
## <a name="remarks"></a>설명  
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) 메서드가 반환 되는 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) 가능한 구조의 공용 구조체를 포함 하는 구조는 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) 구조. `dwKind` 필드를 `DEBUG_ADDRESS_UNION` 포함 구조체는 `ADDRESS_KIND` 값 및 공용 구조체 필드를 해석 하는 방법에 설명 합니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
