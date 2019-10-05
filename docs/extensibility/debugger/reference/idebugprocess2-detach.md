---
title: IDebugProcess2::Detach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Detach
helpviewer_keywords:
- IDebugProcess2::Detach
ms.assetid: ee2b9084-2db1-4e49-a1d9-387284b7c3f8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3948ecce15b9b2b2e8b3bf974ecc2277d9fa0360
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353194"
---
# <a name="idebugprocess2detach"></a>IDebugProcess2::Detach
모든 프로세스에서 프로그램을 분리 하 여이 프로세스에서 디버거를 분리 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT Detach( 
   void 
);
```

```csharp
int Detach();
```

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 모든 프로그램 및 프로세스를 계속 실행 되지만 더 이상 디버그 세션의 일부입니다. 분리 한 후 작업이이 프로세스 (및 해당 프로그램)에 대 한 이벤트를 전송 하는 완전 하 고 더 이상 디버그 중입니다.

## <a name="see-also"></a>참고자료
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)