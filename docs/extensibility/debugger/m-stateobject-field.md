---
title: m_stateObject 필드 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95947a1367ea1ddf4aa88689f731971d5c7d0a6c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330841"
---
# <a name="mstateobject-field"></a>m_stateObject 필드
데이터 작업을 사용할지를 나타내는 개체입니다.

 **네임스페이스:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **어셈블리:** mscorlib (에서 *mscorlib.dll*)

 .NET Framework에서이 내부 멤버에 액세스할 수 없는 때문에 다음 구문은 공통 중간 언어 (CIL) 제공 됩니다.

## <a name="syntax"></a>구문

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>설명
 이 `state` 의 매개 변수는 <xref:System.Threading.Tasks.Task.%23ctor%2A> 생성자입니다. 에 대 한 지원 필드 이기도 합니다 <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> 속성입니다.

## <a name="see-also"></a>참고자료
- [Task 클래스](../../extensibility/debugger/task-class-internal-members.md)