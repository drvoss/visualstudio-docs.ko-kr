---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5a489256b14b828fd548b3e2da3c2c02f9d5317
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349576"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> Visual Studio 2015에서 식 계산기를 구현 하는 이러한 방식으로 사용 되지 않습니다. CLR 식 계산기를 구현 하는 방법에 대 한 정보를 참조 하세요 [CLR 식 계산기](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) 하 고 [관리 되는 식 계산기 샘플](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)합니다.

 디버거의 출력 창에 메시지를 표시 하는 식 계산기 (EE)을 사용 하도록 설정 합니다.

## <a name="syntax"></a>구문

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 콜백은 관리 되는 디버그 엔진에 의해 구현 됩니다.

## <a name="notes-for-callers"></a>호출자에 대 한 정보
 디버거의 출력 창에 출력을 전송 하는 식 계산기에서 사용할 수 있습니다.

## <a name="methods"></a>메서드
 이 인터페이스는 다음 메서드를 구현합니다.

|메서드|설명|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|디버거의 출력 창에 지정 된 메시지 문자열을 보냅니다.|

## <a name="requirements"></a>요구 사항
 헤더: Ee.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll