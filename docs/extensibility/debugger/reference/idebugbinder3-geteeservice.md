---
title: IDebugBinder3::GetEEService | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3afc38551dc04e7fc7f6d55df81c5b7248127acd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66327126"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
이 메서드는 요청 된 서비스를 반환합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetEEService(
   [in] GUID        vendor,
   [in] GUID        language,
   [in] GUID        iid,
   [out] IUnknown** ppService
);
```

```csharp
Int GetEEService(
   Guid       vendor,
   Guid       language,
   Guid       iid,
   out object ppService
);
```

## <a name="parameters"></a>매개 변수
`vendor`\
[in] `GUID` (null 값이 허용) 공급 업체입니다.

`language`\
[in] `GUID` 언어 (null 값이 허용).

`iid`\
[in] `IID` 가져오기 위해 서비스입니다.

`ppService`\
[out] 요청 된 서비스에 사용 되는 인터페이스입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 전달 된 `IID` 에 대 한는 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) 인터페이스 (`IID_IEEVisualizerServiceProvider`) 형식 시각화 도우미 서비스를 사용할 경우 참조를 합니다. 식 계산기를 얻을 수 있는 경우는 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) 인터페이스 형식 시각화 도우미를 지원 하도록 합니다. 참조 [시각화 및 데이터 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md) 세부 정보에 대 한 합니다.

## <a name="see-also"></a>참고자료
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
- [데이터 시각화 및 보기](../../../extensibility/debugger/visualizing-and-viewing-data.md)