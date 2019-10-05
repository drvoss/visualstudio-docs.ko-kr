---
title: CONSTRUCTOR_ENUM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONSTRUCTOR_ENUM
helpviewer_keywords:
- CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea240cf33bab70f1488a2aa90fecd71220b1da25
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346448"
---
# <a name="constructorenum"></a>CONSTRUCTOR_ENUM
다양 한 생성자를 선택합니다.

## <a name="syntax"></a>구문

```cpp
typedef enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
} CONSTRUCTOR_ENUM;
```

```csharp
public enum ConstructorMatchOptions {
    crAll       = 0,
    crNonStatic = 1,
    crStatic    = 2
};
```

## <a name="fields"></a>필드
`crAll`\
모든 생성자를 선택합니다.

`crNonStatic`\
Static이 아니고 생성자를 선택합니다.

`crStatic`\
정적 생성자를 선택합니다.

## <a name="remarks"></a>설명
인수로 전달 된 [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) 메서드.

## <a name="requirements"></a>요구 사항
헤더: sh.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)
