---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89f7ecfc79cc2a4279a8ca0fccfc527ef63e603b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66313206"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
지정 된 형식 인수 배열을 필드 인스턴스를 생성 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ConstructInstantiation(
   ULONG32       cArgs,
   IDebugField** ppArgs,
   IDebugField** ppConstructedField
);
```

```csharp
int ConstructInstantiation(
   uint            cArgs,
   IDebugField[]   ppArgs,
   out IDebugField ppConstructedField
);
```

## <a name="parameters"></a>매개 변수
`cArgs`\
[in] 인수 개수는 `ppArgs` 배열입니다.

`ppArgs`\
[in] 형식 인수를 포함 하는 배열입니다. 형식 인수에는 닫힌된 형식 (제네릭이 아닌 또는 완전히 인스턴스화된 제네릭) 이어야 합니다.

`ppConstructedField`\
[out] 반환 된 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 새 필드를 나타내는 인터페이스입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 제약 조건은 확인 하지 않습니다.

## <a name="see-also"></a>참고자료
- [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)