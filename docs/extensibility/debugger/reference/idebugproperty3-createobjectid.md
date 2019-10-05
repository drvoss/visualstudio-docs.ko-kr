---
title: IDebugProperty3::CreateObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ee1d2a66a5ed655c132526c5d73b6673a680c971
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339854"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
다른 모든 속성 간에 고유한 지 확인 하려면이 속성에 대 한 고유 ID를 만듭니다.

## <a name="syntax"></a>구문

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 세션 디버그 관리자에서 다른 모든 속성과 함께이 속성은 고유 하 게 식별 하 고 있는지 확인 하려고 할 때 호출 됩니다. 디버그 엔진 (DE) 다룹니다 속성은 이미 고유 하 게 식별 하는 경우가 아니면이 메서드를 지원 합니다. 반환 하는 경우에 DE이이 메서드를 지원 하지 않습니다, `E_NOTIMPL`합니다.

 모든 고유 ID 사용 하 여 만든 `CreateObjectID` 때 소멸 되는 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) 메서드는;이 또한 끝난 것이 속성을 고유 하 게 식별 해야 합니다.

> [!NOTE]
> DE 고유 Id에 대 한 원하는 모든 작업을 수행할 수 있도록이 고유 ID를 검색할 방법이 없습니다 경우는 `CreateObjectID` 메서드가 호출 됩니다.

## <a name="see-also"></a>참고자료
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)