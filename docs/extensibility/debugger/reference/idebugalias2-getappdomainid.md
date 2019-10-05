---
title: IDebugAlias2::GetAppDomainId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetAppDomainId
- IDebugAlias2::GetAppDomainId
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b40d52c5eedf0defb845f1944acd166d48dca1ee
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338168"
---
# <a name="idebugalias2getappdomainid"></a>IDebugAlias2::GetAppDomainId
응용 프로그램 도메인에 대 한 식별자를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAppDomainId (
   ULONG32* pappDomainId
);
```

```csharp
int GetAppDomainId (
   out uint pappDomainId
);
```

## <a name="parameters"></a>매개 변수
`pappDomainId`\
[out] 응용 프로그램 도메인 식별자를 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 응용 프로그램 다시 시작 될 때마다 응용 프로그램 도메인 식별자 변경 및 새 응용 프로그램 도메인 생성 됩니다.

## <a name="see-also"></a>참고자료
- [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)