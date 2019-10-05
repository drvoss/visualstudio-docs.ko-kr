---
title: IDebugGenericFieldDefinition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2887333789a9a4eae89a9f3f7538cf5b29ba02e7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351247"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
관리 코드 제네릭 형식에 대 한 필드의 정의 나타냅니다.

## <a name="syntax"></a>구문

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>메서드
 이 인터페이스는 다음 메서드를 구현 합니다.

|메서드|설명|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|지정 된 형식 인수 배열을 필드 인스턴스를 생성 합니다.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|매개 변수 개수를 지정 된 형식 매개 변수를 검색 합니다.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|일반 필드와 연결 된 형식 매개 변수 개수를 검색 합니다.|

## <a name="requirements"></a>요구 사항
 헤더: Sh.h

 네임스페이스: Microsoft.VisualStudio.Debugger.Interop

 어셈블리: Microsoft.VisualStudio.Debugger.Interop.dll