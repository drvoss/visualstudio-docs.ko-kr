---
title: IDebugExtendedField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExtendedField interface
ms.assetid: b491499c-af57-47da-87d6-34b7398f6591
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a9e8f8e8414b6066bb8a407449a4b588d948bc4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333212"
---
# <a name="idebugextendedfield"></a>IDebugExtendedField
관리 코드 제네릭을 지원에 사용할 수 있는 필드의 종류를 확장 합니다.

## <a name="syntax"></a>구문

```
IDebugExtendedField : IDebugField
```

## <a name="methods"></a>메서드
 메서드 외에도 합니다 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 인터페이스에서이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)|지정 된 확장된 필드 종류를 검색합니다.|
|[IsClosedType](../../../extensibility/debugger/reference/idebugextendedfield-isclosedtype.md)|필드 닫힌된 형식을 나타내는지 여부를 확인 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll