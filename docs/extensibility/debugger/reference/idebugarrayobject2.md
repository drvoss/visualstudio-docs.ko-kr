---
title: IDebugArrayObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e35e012139b7df261f25ea524d0b13abf63b555e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349686"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 관리 되는 배열 개체를 나타내며 식 계산기 (EE) 배열에 대 한 기본 인덱스 (하위 범위)를 확인할 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 관리 되는 디버그 엔진 (DE)에 의해 구현 됩니다.

## <a name="methods"></a>메서드
 메서드 외에도 합니다 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) 인터페이스에서이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|배열의 차원 수를 지정 하는 각 인덱스에 대 한 기본 인덱스 (하위 범위)를 검색 합니다.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|배열에 정의 된 기본 인덱스 (하한값) 하는 경우를 결정 합니다.|

## <a name="remarks"></a>설명
 식 계산기를이 인터페이스를 사용 하 여 관리 되는 배열에서 구문 분석 트리를 나타냅니다.

## <a name="requirements"></a>요구 사항
 헤더: Ee.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll