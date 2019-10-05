---
title: IDebugPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker interface
ms.assetid: 8b7f6685-a3c5-4355-b706-c1b574f6ff84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 991480886c2c43c330ce37561d383ffdc420e214
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340361"
---
# <a name="idebugportpicker"></a>IDebugPortPicker
포트를 선택 하기 위한 사용자 지정된 UI를 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugPortPicker : IUnknown
```

## <a name="notes-for-implementers"></a>구현자 참고 사항
 이 인터페이스는 포트 공급자가 구현 됩니다. 포트 공급자 없거나 CLSID로 노출 하 고 가리키는 하 여 해당 포트 선택을 정의 `metricPortPickerCLSID` 노출 된 CLSID에 메트릭.

## <a name="methods"></a>메서드
 다음 표에서의 메서드를 보여 줍니다. `IDebugPortPicker`합니다.

|메서드|설명|
|------------|-----------------|
|[DisplayPortPicker](../../../extensibility/debugger/reference/idebugportpicker-displayportpicker.md)|사용자가 포트를 선택할 수 있도록 지정 된 대화 상자가 표시 됩니다.|
|[SetSite](../../../extensibility/debugger/reference/idebugportpicker-setsite.md)|서비스 공급자를 설정합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Msdbg.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll