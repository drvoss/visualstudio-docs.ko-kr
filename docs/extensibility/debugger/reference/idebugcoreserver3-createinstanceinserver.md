---
title: IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7e74ea66f5b8ecd04acfbc2617f91bcaf0f7ecbd
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66332408"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
서버에서 디버그 엔진의 인스턴스를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateInstanceInServer(
   LPCWSTR  szDll,
   WORD     wLangId,
   REFCLSID clsidObject,
   REFIID   riid,
   void**   ppvObject
);
```

```csharp
int CreateInstanceInServer(
   string     szDll,
   ushort     wLangID,
   ref Guid   clsidObject,
   ref Guid   riid,
   out IntPtr ppvObject
);
```

## <a name="parameters"></a>매개 변수
`szDll`\
[in] 에 지정 된 CLSID를 구현 하는 dll에 대 한 경로 `clsidObject` 매개 변수입니다. 이것이 `NULL`, 다음 COM의 `CoCreateInstance` 함수를 호출 합니다.

`wLangId`\
[in] 디버그 엔진의 로캘입니다. 이 경우 0를 수 있습니다 합니다 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) 메서드를 호출 해야 합니다.

`clsidObject`\
[in] 만들려는 디버그 엔진의 CLSID입니다.

`riid`\
[in] 클래스 개체에서 검색할 특정 인터페이스의 인터페이스 ID입니다.

`ppvObject`\
[out] `IUnknown` 인스턴스화된 개체의 인터페이스입니다. 캐스트 또는이 개체는 원하는 인터페이스를 마샬링하십시오.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="see-also"></a>참고자료
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
- [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)