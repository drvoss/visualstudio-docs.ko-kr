---
title: FIELD_MODIFIERS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FIELD_MODIFIERS
helpviewer_keywords:
- FIELD_MODIFIERS enumeration
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bd25a3cb5b2d074e989b47f33513e05538868759
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203042"
---
# <a name="fieldmodifiers"></a>FIELD_MODIFIERS
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

필드 형식에 대 한 한정자를 지정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```csharp  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## <a name="members"></a>멤버  
 FIELD_MOD_ACCESS_TYPE  
 필드에 액세스할 수 없습니다 나타냅니다.  
  
 FIELD_MOD_ACCESS_PUBLIC  
 필드에 대 한 공용 액세스에 있음을 나타냅니다.  
  
 FIELD_MOD_ACCESS_PROTECTED  
 필드에 보호 된 액세스 권한을 나타냅니다.  
  
 FIELD_MOD_ACCESS_PRIVATE  
 필드에 대 한 개인 액세스 있음을 나타냅니다.  
  
 FIELD_MOD_NOMODIFIERS  
 필드 한정자가 없습니다에 있음을 나타냅니다.  
  
 FIELD_MOD_STATIC  
 정적 필드 임을 나타냅니다.  
  
 FIELD_MOD_CONSTANT  
 필드는 상수를 나타냅니다.  
  
 FIELD_MOD_TRANSIENT  
 필드 일시적 임을 나타냅니다.  
  
 FIELD_MOD_VOLATILE  
 Volatile 필드 임을 나타냅니다.  
  
 FIELD_MOD_ABSTRACT  
 필드 추상 임을 나타냅니다.  
  
 FIELD_MOD_NATIVE  
 기본 필드 임을 나타냅니다.  
  
 FIELD_MOD_SYNCHRONIZED  
 필드는 동기화 하는 것을 나타냅니다.  
  
 FIELD_MOD_VIRTUAL  
 가상 필드 임을 나타냅니다.  
  
 FIELD_MOD_INTERFACE  
 인터페이스 필드 임을 나타냅니다.  
  
 FIELD_MOD_FINAL  
 마지막 필드 임을 나타냅니다.  
  
 FIELD_MOD_SENTINEL  
 필드는 sentinel 임을 나타냅니다.  
  
 FIELD_MOD_INNERCLASS  
 필드는 내부 클래스를 나타냅니다.  
  
 FIELD_TYPE_OPTIONAL  
 필드 선택 사항임을 나타냅니다.  
  
 FIELD_MOD_BYREF  
 필드 참조 인수 임을 나타냅니다. 이 특히 메서드 인수입니다.  
  
 FIELD_MOD_HIDDEN  
 필드 또는 숨겨진 다른 컨텍스트에 나오는 수 해야 나타냅니다. 예를 들어 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 정적 지역 변수입니다.  
  
 FIELD_MOD_MARSHALASOBJECT  
 필드를 사용 하 여 개체를 나타냄을 `IUnknown` 인터페이스입니다.  
  
 FIELD_MOD_SPECIAL_NAME  
 필드에는 특별 한 이름, 예를 들어 나타냅니다 `.ctor` 생성자에 대 한 ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 만).  
  
 FIELD_MOD_HIDEBYSIG  
 필드에 있음을 나타냅니다 합니다 `Overloads` 적용할 키워드 ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 만).  
  
 FIELD_MOD_WRITEONLY  
 쓰기 전용 필드 임을 나타냅니다. 이 값에 포함 되지 않습니다 `FIELD_MOD_ALL`함수 실행에만 이러한 쓰기 전용 필드를 사용 하는 합니다. 사용자에 대 한 명시적으로 요청 해야 `FIELD_MOD_WRITEONLY` 필드입니다.  
  
 FIELD_MOD_ACCESS_MASK  
 필드 액세스에 대 한 마스크를 나타냅니다.  
  
 FIELD_MOD_MASK  
 필드 한정자에 대 한 마스크를 나타냅니다.  
  
## <a name="remarks"></a>설명  
 에 사용 되는 합니다 `dwModifiers` 의 멤버는 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) 구조입니다.  
  
 이러한 값은 또한 전달 된 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md) 특정 필드에 대해 필터링 하는 방법입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>관련 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
