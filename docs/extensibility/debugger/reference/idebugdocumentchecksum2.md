---
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b4bfc51595e6414a3760d4e57ab6f9791259f83
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66341294"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
디버그 문서에 대해 체크섬을 나타내며 체크섬 구성 요소 간에 전달 수 있습니다.

## <a name="syntax"></a>구문

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스를 노출 하는 모든 구성 요소에서 구현할 수 있습니다 합니다 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) 인터페이스입니다. 그러나 기호 파일 (*.pdb)에 포함 된 체크섬을 IDE에 다시 전달 하 고 소스를 찾을 때 사용 될 수 있도록 디버그 엔진에서 구현 주로 됩니다.

## <a name="methods"></a>메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugDocumentChecksum2`합니다.

|메서드|설명|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|사용 하는 바이트의 최대 수를 지정 된 문서 체크섬과 알고리즘 식별자를 검색 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll