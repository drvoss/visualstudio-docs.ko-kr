---
title: DBG_ATTRIB_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DBG_ATTRIB_FLAGS
helpviewer_keywords:
- DBGPROP_ATTRIB_FLAGS enumerations
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fde7ac384a6b2de293fc9baf0075438c9c609236
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346291"
---
# <a name="dbg_attrib_flags"></a>DBG_ATTRIB_FLAGS
에 대 한 다양 한 특성에 설명 합니다는 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 요소나 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) 인터페이스입니다. 멤버는 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) 구조입니다.

## <a name="syntax"></a>구문

```cpp
#define DBG_ATTRIB_NONE                 0x0000000000000000,
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,

// Attributes about the object itself

#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,

// Attributes about the value of the object

#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,

// Attributes about field access types for the object

#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,

// Attributes for the storage types of the object

#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,

// Attributes for the type modifiers on the object

#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,

// Attributes that describe the type of object

#define DBG_ATTRIB_DATA                 0x0000010000000000,
#define DBG_ATTRIB_METHOD               0x0000020000000000,
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,
#define DBG_ATTRIB_CLASS                0x0000080000000000,
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,

// Miscellaneous attributes

#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000

typedef UINT64 DBG_ATTRIB_FLAGS;
```

```csharp
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,

// Attributes about the object itself

public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,

// Attributes about the value of the object

public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,

// Attributes about field access types for the object

public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,

// Attributes for the storage types of the object

public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,

// Attributes for the type modifiers on the object

public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,

// Attributes that describe the type of object

public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,

// Miscellaneous attributes

public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000
```

## <a name="members"></a>멤버
 `DBG_ATTRIB_NONE`\
 특성이 없음을 나타냅니다.

 `DBG_ATTRIB_ALL`\
 모든 특성을 나타냅니다.

 `DBG_ATTRIB_OBJ_IS_EXPANDABLE`\
 참조 또는 속성에 자식이 있음을 나타냅니다.

 `DBG_ATTRIB_OBJ_HAS_ID`\
 이 개체의 ID가 생성 되었음을 나타냅니다.

 `DBG_ATTRIB_OBJ_CAN_HAVE_ID`\
 이 개체의 ID를 만들 수 있음을 나타냅니다.

 `DBG_ATTRIB_VALUE_READONLY`\
 값이 읽기 전용임을 나타냅니다.

 `DBG_ATTRIB_VALUE_ERROR`\
 오류 값 임을 나타냅니다.

 `DBG_ATTRIB_VALUE_SIDE_EFFECT`\
 평가 부작용을 나타냅니다.

 `DBG_ATTRIB_OVERLOADED_CONTAINER`\
 이 속성은 실제로 오버 로드의 컨테이너를 나타냅니다.

 `DBG_ATTRIB_VALUE_BOOLEAN`\
 함을 값 `DEBUG_PROPERTY_INFO::bstrValue` 부울입니다.

 `DBG_ATTRIB_VALUE_BOOLEAN_TRUE`\
 함을 값 `DEBUG_PROPERTY_INFO::bstrValue` 부울 및 `TRUE`합니다.

 `DBG_ATTRIB_VALUE_INVALID`\
 `DEBUG_PROPERTY_INFO::bstrValue`의 값이 유효하지 않음을 나타냅니다.

 `DBG_ATTRIB_VALUE_NAT`\
 함을 값 `DEBUG_PROPERTY_INFO::bstrValue` 는 "*것 없습니다*" (NAT). NAT는 지연 된 잘못 된 예외를 나타내는 Intel 64 비트 프로세서의 레지스터 플래그를 설명 합니다.

 `DBG_ATTRIB_VALUE_AUTOEXPANDED`\
 함을 값 `DEBUG_PROPERTY_INFO::bstrValue` 자동 확장 되었습니다 수 있습니다.

 `DBG_ATTRIB_VALUE_TIMEOUT`\
 평가 시간이 초과 되었습니다를 나타냅니다.

 `DBG_ATTRIB_VALUE_RAW_STRING`\
 함을 값 `DEBUG_PROPERTY_INFO::bstrValue` 원시 문자열로 나타낼 수 있습니다.

 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER`\
 이 속성에 연결 된 하나 이상의 사용자 지정 뷰어 있음을 나타냅니다.

 `DBG_ATTRIB_ACCESS_NONE`\
 에 있는 개체를 나타냅니다 `public`, `private`, 또는 `protected` 액세스를 입력 합니다.

 `DBG_ATTRIB_ACCESS_PUBLIC`\
 공용 액세스 권한이 있는 개체를 나타냅니다.

 `DBG_ATTRIB_ACCESS_PRIVATE`\
 개인 액세스 권한이 있는 개체를 나타냅니다.

 `DBG_ATTRIB_ACCESS_PROTECTED`\
 보호 액세스 권한이 있는 개체를 나타냅니다.

 `DBG_ATTRIB_ACCESS_FINAL`\
 최종 액세스 권한이 있는 개체를 나타냅니다.

 `DBG_ATTRIB_ACCESS_ALL`\
 마스크의 액세스 특성을 추출할 `DBG_ATTRIB_FLAGS`합니다.

 `DBG_ATTRIB_STORAGE_NONE`\
 저장소 형식이 지정 되지 않은 임을 나타냅니다.

 `DBG_ATTRIB_STORAGE_GLOBAL`\
 전역 스토리지를 나타냅니다.

 `DBG_ATTRIB_STORAGE_STATIC`\
 정적 스토리지를 나타냅니다.

 `DBG_ATTRIB_STORAGE_REGISTER`\
 레지스터에 저장소를 나타냅니다.

 `DBG_ATTRIB_STORAGE_ALL`\
 저장소 특성을 추출 하는 마스크 `DBG_ATTRIB_FLAGS`합니다.

 `DBG_ATTRIB_TYPE_NONE`\
 어떠한 형식 한정자 임을 나타냅니다.

 `DBG_ATTRIB_TYPE_VIRTUAL`\
 개체의 형식 가상 임을 나타냅니다.

 `DBG_ATTRIB_TYPE_CONSTANT`\
 개체 형식이 상수임을 나타냅니다.

 `DBG_ATTRIB_TYPE_SYNCHRONIZED`\
 개체 유형의 동기화 있는지를 나타냅니다.

 `DBG_ATTRIB_TYPE_VOLATILE`\
 개체의 형식 일시적 임을 나타냅니다.

 `DBG_ATTRIB_TYPE_ALL`\
 형식 특성을 추출 하는 마스크 `DBG_ATTRIB_FLAGS`합니다.

 `DBG_ATTRIB_DATA`\
 이 개체는 데이터 필드를 나타냅니다.

 `DBG_ATTRIB_METHOD`\
 이 개체는 메서드를 나타냅니다.

 `DBG_ATTRIB_PROPERTY`\
 이 개체 속성 임을 나타냅니다.

 `DBG_ATTRIB_CLASS`\
 이 개체는 클래스를 나타냅니다.

 `DBG_ATTRIB_BASECLASS`\
 이 개체는 기본 클래스를 나타냅니다.

 `DBG_ATTRIB_INTERFACE`\
 이 개체는 인터페이스를 나타냅니다.

 `DBG_ATTRIB_INNERCLASS`\
 이 개체는 내부 클래스를 나타냅니다.

 `DBG_ATTRIB_MOSTDERIVED`\
 이 개체가 나타내는 '*가장 많이 파생 된*'. 용어 "*가장 많이 파생 된*" 개체의 실제 형식 및 해당 참조 형식이 아닌 것을 의미 합니다.

 `DBG_ATTRIB_CHILD_ALL`\
 마스크는 나타냅니다 `DBG_ATTRIB_DATA` 를 통해 `DBG_ATTRIB_MOSTDERIVED`합니다.

 `DBG_ATTRIB_MULTI_CUSTOM_VIEWERS`\
 개체에 연결 된 여러 사용자 지정 뷰어 있음을 나타냅니다.

## <a name="remarks"></a>설명

> [!NOTE]
> 이 열거형의 값을 C#에 대 한 어셈블리에서 실제로 정의 되지 않습니다. 대신 정의 소스 파일을 복사 해야 합니다.

 이러한 플래그에 대 한 인수로 전달 하는 경우 예를 들어 개체의 자식을 필터링 할 수도 있습니다 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)합니다. 비트 값을 결합할 수 있습니다 `OR`합니다.

 합니다 `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` 플래그를 표시 하는 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] 가져오려고 합니다 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) 에서 인터페이스를 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) 인터페이스를 호출 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) 사용자 지정 뷰어 목록에 대 한 합니다.

## <a name="requirements"></a>요구 사항
 헤더: msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)