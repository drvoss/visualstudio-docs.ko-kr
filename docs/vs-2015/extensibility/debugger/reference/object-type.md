---
title: OBJECT_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc23045fa70554133eba3a7f1326681bf31ea379
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205149"
---
# <a name="objecttype"></a>OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

식 계산기에서 개체의 형식을 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```csharp  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## <a name="members"></a>멤버  
 OBJECT_TYPE_BOOLEAN  
 부울 개체 임을 나타냅니다.  
  
 OBJECT_TYPE_CHAR  
 개체는 문자 인지를 나타냅니다.  
  
 OBJECT_TYPE_I1  
 개체는 1 바이트 부호 있는 정수를 나타냅니다.  
  
 OBJECT_TYPE_U1  
 개체는 1 바이트 부호 없는 정수를 나타냅니다.  
  
 OBJECT_TYPE_I2  
 개체는 2 바이트 부호 있는 정수를 나타냅니다.  
  
 OBJECT_TYPE_U2  
 개체는 2 바이트 부호 없는 정수를 나타냅니다.  
  
 OBJECT_TYPE_I4  
 개체는 4 바이트 부호 있는 정수를 나타냅니다.  
  
 OBJECT_TYPE_U4  
 개체는 4 바이트 부호 없는 정수를 나타냅니다.  
  
 OBJECT_TYPE_I8  
 개체는 8 비트 부호 있는 정수를 나타냅니다.  
  
 OBJECT_TYPE_U8  
 개체는 8 비트 부호 없는 정수를 나타냅니다.  
  
 OBJECT_TYPE_R4  
 개체는 4 바이트 부동 소수점 숫자를 나타냅니다.  
  
 OBJECT_TYPE_R8  
 개체는 8 바이트 부동 소수점 숫자를 나타냅니다.  
  
 OBJECT_TYPE_OBJECT  
 개체는 개체 임을 나타냅니다.  
  
 OBJECT_TYPE_NULL  
 개체가 NULL 임을 나타냅니다.  
  
 OBJECT_TYPE_CLASS  
 개체 클래스 임을 나타냅니다.  
  
## <a name="remarks"></a>설명  
 인수로 전달 합니다 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) 하 고 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) 메서드.  
  
## <a name="requirements"></a>요구 사항  
 헤더: ee.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)
