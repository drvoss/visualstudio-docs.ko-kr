---
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 951f0dde4dbd57ac18269adedd77c8f6d7ccdd5e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410098"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 숫자 변수에 별칭을 나타내며 식 계산기 (EE) 응용 프로그램 도메인 별칭을 가져올 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 관리 되는 디버그 엔진 (DE)에 의해 구현 됩니다.

## <a name="methods"></a>메서드
 메서드 외에도 합니다 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) 인터페이스에서이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|응용 프로그램 도메인에 대 한 식별자를 검색합니다.|

## <a name="remarks"></a>설명
 별칭은 문자열 형식의 예를 들어 1001 # # 문자를 뒤에 10 진수입니다.

## <a name="requirements"></a>요구 사항
 헤더: Ee.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll