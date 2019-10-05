---
title: FIELD_KIND | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- FIELD_KIND
helpviewer_keywords:
- FIELD_KIND enumeration
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab972df2cf1b382498d2e57a5ae2e978c7230a34
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692871"
---
# <a name="fieldkind"></a>FIELD_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

에 포함 된 필드의 종류를 지정 된 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 개체입니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```csharp  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## <a name="members"></a>멤버  
 FIELD_KIND_TYPE  
 필드에만 형식 인지를 나타냅니다.  
  
 FIELD_KIND_SYMBOL  
 필드 형식, 이름 및 기타 정보를 사용 하 여 기호를 나타냅니다.  
  
 FIELD_TYPE_PRIMITIVE  
 필드는 기본 데이터 형식을 나타냅니다.  
  
 FIELD_TYPE_STRUCT  
 필드는 구조체 임을 나타냅니다.  
  
 FIELD_TYPE_CLASS  
 필드는 클래스를 나타냅니다.  
  
 FIELD_TYPE_INTERFACE  
 인터페이스 필드 임을 나타냅니다.  
  
 FIELD_TYPE_UNION  
 공용 구조체 필드 임을 나타냅니다.  
  
 FIELD_TYPE_ARRAY  
 필드는 배열 임을 나타냅니다.  
  
 FIELD_TYPE_METHOD  
 필드는 메서드를 나타냅니다.  
  
 FIELD_TYPE_BLOCK  
 블록 필드 임을 나타냅니다.  
  
 FIELD_TYPE_POINTER  
 필드에 대 한 포인터 임을 나타냅니다.  
  
 FIELD_TYPE_ENUM  
 열거형된 데이터 형식의 필드 임을 나타냅니다.  
  
 FIELD_TYPE_LABEL  
 레이블 필드 임을 나타냅니다.  
  
 FIELD_TYPE_TYPEDEF  
 필드는 typedef 임을 나타냅니다.  
  
 FIELD_TYPE_BITFIELD  
 필드는 비트 필드 임을 나타냅니다.  
  
 FIELD_TYPE_NAMESPACE  
 네임 스페이스 필드 임을 나타냅니다.  
  
 FIELD_TYPE_MODULE  
 필드는 모듈 임을 나타냅니다.  
  
 FIELD_TYPE_DYNAMIC  
 동적 필드 임을 나타냅니다.  
  
 FIELD_TYPE_PROP  
 필드 속성 임을 나타냅니다.  
  
 FIELD_TYPE_INNERCLASS  
 필드는 내부 클래스를 나타냅니다.  
  
 FIELD_TYPE_REFERENCE  
 필드에 대 한 참조 임을 나타냅니다.  
  
 FIELD_TYPE_EXTENDED  
 나중에 사용하기 위해 예약되어 있습니다.  
  
 FIELD_SYM_MEMBER  
 멤버가 필드 임을 나타냅니다.  
  
 FIELD_SYM_LOCAL  
 로컬 필드 임을 나타냅니다.  
  
 FIELD_SYM_PARAMETER  
 매개 변수 필드 임을 나타냅니다.  
  
 FIELD_SYM_THIS  
 필드 "this"이 포인터 임을 나타냅니다.  
  
 FIELD_SYM_GLOBAL  
 전역 필드 임을 나타냅니다.  
  
 FIELD_SYM_PROP_GETTER  
 필드 속성을 검색 합니다를 나타냅니다.  
  
 FIELD_SYM_PROP_SETTER  
 필드 속성을 설정 함을 나타냅니다.  
  
 FIELD_SYM_EXTENDED  
 나중에 사용하기 위해 예약되어 있습니다.  
  
 FIELD_KIND_MASK  
 필드 종류에 대 한 마스크를 나타냅니다.  
  
 FIELD_TYPE_MASK  
 필드 형식에 대 한 마스크를 나타냅니다.  
  
 FIELD_SYM_MASK  
 기호 정보에 대 한 마스크를 나타냅니다.  
  
## <a name="remarks"></a>설명  
 호출에서 반환 된 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 메서드.  
  
 필드의 종류에 따라 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 에 대해 호출할 수는 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스의 구체적인 형식에 대 한 인터페이스입니다. 예를 들어 경우 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) 반환 `FIELD_TYPE_METHOD`를 호출할 수 있습니다 `QueryInterface` 필자에`DebugField` 가져오려고 합니다 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) 인터페이스입니다.  
  
## <a name="requirements"></a>요구 사항  
 헤더: sh.h  
  
 네임스페이스: Microsoft.VisualStudio.Debugger.Interop  
  
 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>참고 항목  
 [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
