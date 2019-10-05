---
title: IDebugArrayObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d68b0db20150bd81a9b2b4aef29c78701a6bc8ee
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440695"
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