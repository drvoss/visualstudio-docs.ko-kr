---
title: IDebugProcess2::GetInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetInfo
helpviewer_keywords:
- IDebugProcess2::GetInfo
ms.assetid: 46021dce-bb97-46c3-b0cc-e5b3b68acc35
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e6227e8a4397dac03e9ecc70eedf2b902888cdbb
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353150"
---
# <a name="idebugprocess2getinfo"></a>IDebugProcess2::GetInfo
프로세스에 대 한 설명을 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetInfo(
   PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO*        pProcessInfo
);
```

```csharp
int GetInfo(
   enum_PROCESS_INFO_FIELDS  Fields,
   PROCESS_INFO[]            pProcessInfo
);
```

## <a name="parameters"></a>매개 변수
`Fields`\
[in] 값의 조합 합니다 [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md) 의 필드를 지정 하는 열거형을 `pProcessInfo` 입력할 매개 변수는 합니다.

`pProcessInfo`\
[out] A [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) 구조는이 프로세스에 대 한 설명을 채워집니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고자료
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [PROCESS_INFO_FIELDS](../../../extensibility/debugger/reference/process-info-fields.md)
- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)