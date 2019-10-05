---
title: AsyncTaskMethodBuilder&lt;TResult&gt; 구조-내부 멤버 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c944671b3bdb42f72928822903ccb05742401f7e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350980"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; 구조-내부 멤버
내부 멤버에 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 클래스입니다. 이 클래스에 대 한 일반 정보에 대 한 참조를 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 참조 항목입니다.

 **네임스페이스:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **어셈블리:** mscorlib (mscorlib.dll)

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없는 때문에 다음 구문은 공통 중간 언어 (CIL) 제공 됩니다.

## <a name="syntax"></a>구문

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>내부 멤버

|이름|설명|
|----------|-----------------|
|[ObjectIdForDebugger 속성](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|이 작성기 디버거를 고유 하 게 식별 하는 데 사용할 수 있는 개체를 가져옵니다.|
|[m_task 필드](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|초기화 지연 작업 작성 나타냅니다.|

## <a name="see-also"></a>참고자료
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [.NET Framework에 대 한 병렬 확장 기능 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)