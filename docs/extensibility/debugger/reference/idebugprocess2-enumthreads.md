---
title: IDebugProcess2::EnumThreads | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::EnumThreads
helpviewer_keywords:
- IDebugProcess2::EnumThreads
ms.assetid: 05677385-7a7f-4545-8438-af00dde85db0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 664f4264fd12106fef0650a31a888470e09a3154
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353175"
---
# <a name="idebugprocess2enumthreads"></a>IDebugProcess2::EnumThreads
프로세스에서 실행 중인 모든 스레드의 목록을 검색 합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT EnumThreads(
   IEnumDebugThreads2** ppEnum
);
```

```csharp
int EnumThreads(
   out IEnumDebugThreads2 ppEnum
);
```

## <a name="parameters"></a>매개 변수
`ppEnum`\
[out] 반환 된 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md) 프로세스에서 모든 프로그램에서 모든 스레드의 목록을 포함 하는 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 각 프로그램에서 실행 중인 스레드를 열거 하 고 결합 하 여 스레드는 프로세스 보기. 여러 프로그램에 단일 스레드를 실행할 수 있습니다. 이 메서드는 스레드를 한 번만 열거합니다.

 이 메서드는 중복 항목 없이 프로세스의 스레드 목록을 표시합니다. 그렇지 않은 경우 특정 프로그램에서 실행 중인 스레드를 열거 하려면 사용 합니다 [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) 메서드.

## <a name="see-also"></a>참고자료
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)