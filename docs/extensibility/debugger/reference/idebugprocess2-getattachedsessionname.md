---
title: IDebugProcess2::GetAttachedSessionName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d14e76e576aaf3e467ab24083d445c9d9fc5214
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353158"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
이 프로세스를 디버깅 하는 세션의 이름을 가져옵니다. IDE는 사용자에 게 특정 컴퓨터에서 특정 프로세스를 디버깅 하는이 정보를 표시할 수 있습니다.

> [!NOTE]
> 이 메서드는 사용 되지 않으며 해당 구현이 항상 반환 `E_NOTIMPL`합니다.

## <a name="syntax"></a>구문

```
HRESULT GetAttachedSessionName(
   BSTR* pbstrSessionName
);
```

## <a name="parameters"></a>매개 변수
`pbstrSessionName`\

## <a name="return-value"></a>반환 값
 이 메서드는 항상 반환 `E_NOTIMPL`합니다.

## <a name="see-also"></a>참고자료
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)