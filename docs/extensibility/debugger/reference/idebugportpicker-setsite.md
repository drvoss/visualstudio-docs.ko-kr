---
title: IDebugPortPicker::SetSite | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPortPicker::SetSite
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33d6d12bd21a6ab208fed019c1e0f763bce86724
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340355"
---
# <a name="idebugportpickersetsite"></a>IDebugPortPicker::SetSite
서비스 공급자를 설정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT SetSite(
   IServiceProvider * pSP
);
```

```csharp
public int SetSite(
   IServiceProvider pSP
);
```

## <a name="parameters"></a>매개 변수
`pSP`\
[in] 서비스 공급자의 인터페이스에 대 한 참조입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 다른 메서드가 호출 되기 전에 호출 됩니다.

## <a name="see-also"></a>참고자료
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)