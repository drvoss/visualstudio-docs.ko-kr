---
title: IEEVisualizerService::GetValueDisplayStringCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20e09dad1d87df646d1dc8ef7509842b49a8cdaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66308916"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
지정 된 속성 또는 필드에 대해 표시할 문자열 값을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

## <a name="parameters"></a>매개 변수
`displayKind`\
[in] 값을 [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) 열거형입니다.

`propertyOrField`\
[in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 속성 또는 필드를 나타내는 인터페이스입니다.

`pcelt`\
[out] 표시할 문자열 값의 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고자료
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)