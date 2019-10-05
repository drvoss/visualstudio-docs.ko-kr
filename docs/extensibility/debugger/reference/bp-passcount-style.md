---
title: BP_PASSCOUNT_STYLE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_PASSCOUNT_STYLE
helpviewer_keywords:
- BP_PASSCOUNT_STYLE structure
ms.assetid: 0a647047-e2d5-4724-a0b8-68108425ecad
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4ea44ef70ba086a58454891987711ce7cca643e8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353057"
---
# <a name="bppasscountstyle"></a>BP_PASSCOUNT_STYLE
중단점이 발생 하는 중단점 패스 개수와 연결 된 조건을 지정 합니다.

## <a name="syntax"></a>구문

```cpp
enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
typedef DWORD BP_PASSCOUNT_STYLE;
```

```csharp
public enum enum_BP_PASSCOUNT_STYLE {
    BP_PASSCOUNT_NONE             = 0x0000,
    BP_PASSCOUNT_EQUAL            = 0x0001,
    BP_PASSCOUNT_EQUAL_OR_GREATER = 0x0002,
    BP_PASSCOUNT_MOD              = 0x0003
};
```

## <a name="fields"></a>필드
`BP_PASSCOUNT_NONE`\
중단점 단계 수 스타일이 없습니다를 지정합니다.

`BP_PASSCOUNT_EQUAL`\
중단점 패스 개수 스타일과 동일 하 게 설정 합니다. 중단점은 중단점에 적중 횟수 전달 수 인 경우 발생 합니다.

`BP_PASSCOUNT_EQUAL_OR_GREATER`\
중단점 전달 수 스타일 크거나을 설정 합니다. 중단점은 중단점에 적중 횟수 전달 수보다 크거나 같은 경우에 발생 합니다.

`BP_PASSCOUNT_MOD`\
지정 된 모듈로 전달할 수 있습니다. 예를 들어 패스 횟수가 형식의 `BP_PASSCOUNT_MOD` 패스 개수 값은 4, 적중된 횟수는 4의 배수가 될 때마다 중단점이 발생 합니다.

## <a name="remarks"></a>설명
에 사용 되는 합니다 `stylePassCount` 의 멤버는 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) 구조체의 멤버를 다시를 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) 및 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) 구조입니다.

## <a name="requirements"></a>요구 사항
헤더: msdbg.h

네임스페이스: Microsoft.VisualStudio.Debugger.Interop

어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>참고자료
- [열거형](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
