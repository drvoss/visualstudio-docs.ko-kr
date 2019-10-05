---
title: IDebugProgramNode2::GetEngineInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e3e24c2c326f7ebc7427da3804f17f1f75aeef4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205740"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
이름 및 프로그램을 실행 하는 디버그 엔진 (DE)의 식별자를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetEngineInfo ( 
   BSTR* pbstrEngine,
   GUID* pguidEngine
);
```

```csharp
int GetEngineInfo(
   out string pbstrEngine,
   out Guid pguidEngine
);
```

#### <a name="parameters"></a>매개 변수
 `pbstrEngine`

 [out] 프로그램을 실행 하는 DE의 이름을 반환 합니다 (C++-특정: 호출자 엔진의 이름을 원하는 임을 나타내는 null 포인터 수)입니다.

 `pguidEngine`

 [out] 프로그램을 실행 하는 DE의 전역 고유 식별자를 반환 합니다 (C++-특정: 호출자가 엔진의 GUID에 관심이 없는 나타내는 null 포인터 수)입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>관련 항목
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)