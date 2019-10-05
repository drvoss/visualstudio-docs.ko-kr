---
title: IDebugGenericFieldInstance | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 189d670892b50958edff3b256874441aebd72be5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330497"
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
관리 코드 제네릭 형식에 대 한 필드의 인스턴스를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugGenericFieldInstance : IUnknown
```

## <a name="methods"></a>메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|이 인스턴스에 대 한 형식 매개 변수 인수를 검색합니다.|
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|이 인스턴스에 대 한 매개 변수 인수 형식의 수를 반환합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll