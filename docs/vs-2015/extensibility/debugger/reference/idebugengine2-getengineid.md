---
title: IDebugEngine2::GetEngineID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ab0bfe52090ab719bbc2fbd442b9b609b5991e84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68195992"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
디버그 엔진 (DE)의 GUID를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

#### <a name="parameters"></a>매개 변수
`pguidEngine`

 [out] DE의 GUID를 반환합니다.

## <a name="return-value"></a>반환 값
성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
일반적인 Guid의 일부의 예로 `guidScriptEng`, `guidNativeEng`, 또는 `guidSQLEng`합니다. 새 디버그 엔진을 id에 대 한 고유한 GUID를 만듭니다.

## <a name="example"></a>예제
다음 예제에서는 간단한에 대 한이 메서드를 구현 하는 방법을 보여 줍니다 `CEngine` 를 구현 하는 개체를 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) 인터페이스입니다.

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>관련 항목
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
