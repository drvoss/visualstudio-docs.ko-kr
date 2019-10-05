---
title: IDebugContainerField::EnumFields | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a6d3edeb677af728b1a0fd0e9cf8685e7919d79e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317938"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
컨테이너의 필드에 대 한 열거자를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>매개 변수
`dwKindFilter`\
[in] 조합을 [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) 열거할 필드를 선택 하는 상수입니다. 필드 종류는 저장소 유형, 클래스 또는 기본 형식 또는 특정 정보와 같은, 로컬, 매개 변수를 "this"이 포인터 등을 설명할 수 있습니다.

`dwModifiersFilter`\
[in] 조합을 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) 열거할 필드를 선택 하는 상수입니다. 필드 한정자에는 공용 또는 개인 또는 가상, 정적 또는 최종 등의 저장소 정보 등의 액세스 권한을 수 있습니다.

`pszNameFilter`\
[in] 열거할 필드의 이름입니다. 모든 필드는 반환 될 경우 null 값을이 수 있습니다.

`nameMatch`\
[in] 값을 [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) 여부를 검색 하는지 여부를 제어 하는 열거형은 대/소문자 구분 합니다.

`ppEnum`\
[out] 반환 된 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) 필드 목록을 나타내는 개체입니다. 필드가 없는 경우 null 값을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK 또는 반환 S_FALSE 필드가 없는 경우. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 합니다 `dwKindFilter`, `dwModifiersFilter`, 및 `pszNameFilter` 매개 변수 결합할 수 있습니다, 예를 들어, "MyMethod" 라는 모든 공용 가상 메서드를 선택 합니다.

## <a name="see-also"></a>참고자료
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)