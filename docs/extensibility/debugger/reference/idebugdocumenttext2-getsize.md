---
title: IDebugDocumentText2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetSize
helpviewer_keywords:
- IDebugDocumentText2::GetSize
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f382b1d27a83e4493431ac8e6cca3d6aef9dd72
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337372"
---
# <a name="idebugdocumenttext2getsize"></a>IDebugDocumentText2::GetSize
문서의이 위치에서 텍스트의 크기를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetSize( 
   ULONG* pcNumLines,
   ULONG* pcNumChars
);
```

```csharp
int GetSize( 
   ref uint pcNumLines,
   ref uint pcNumChars
);
```

## <a name="parameters"></a>매개 변수
`pcNumLines`\
[out] 텍스트 줄의 수를 반환합니다.

`pcNumChars`\
[out] 텍스트의 문자 수를 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명

 [C++ 만] 특정 값을 원하지 않는 경우 매개 변수에 대해 NULL을 전달 합니다.

 [C# 만] 매개 변수를 모두 지정 해야 합니다.

## <a name="see-also"></a>참고자료
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)