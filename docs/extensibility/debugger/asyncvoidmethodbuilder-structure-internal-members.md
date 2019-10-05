---
title: AsyncVoidMethodBuilder 구조-내부 멤버 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 109f7d0491420ce4f3df2179dad15a582213d439
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350933"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>AsyncVoidMethodBuilder 구조-내부 멤버
내부 멤버에 설명 합니다 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 클래스입니다. 이 클래스에 대 한 일반 정보에 대 한 참조를 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 참조 항목입니다.

 **네임스페이스:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **어셈블리:** mscorlib (mscorlib.dll)

 .NET Framework에서 이러한 내부 멤버에 액세스할 수 없는 때문에 다음 구문은 공통 중간 언어 (CIL) 제공 됩니다.

## <a name="syntax"></a>구문

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>내부 멤버

|이름|설명|
|----------|-----------------|
|[ObjectIdForDebugger 속성](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|이 작성기 디버거를 고유 하 게 식별 하는 데 사용할 수 있는 개체를 가져옵니다.|
|[m_objectIdForDebugger field](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|디버거에서 사용 하 여이 작성기를 고유 하 게 식별 하 여 지연 초기화 된 개체를 나타냅니다.|

## <a name="see-also"></a>참고자료
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [.NET Framework에 대 한 병렬 확장 기능 내부](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)