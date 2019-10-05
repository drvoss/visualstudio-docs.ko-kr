---
title: IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromContext
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromContext method
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ff38d2bd286c0a1ff82aafc3526936447be69056
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66335212"
---
# <a name="idebugsymbolprovidergetaddressesfromcontext"></a>IDebugSymbolProvider::GetAddressesFromContext
이 메서드는 디버그 주소 배열로 문서 컨텍스트를 매핑합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAddressesFromContext( 
   IDebugDocumentContext2* pDocContext,
   BOOL                    fStatmentOnly,
   IEnumDebugAddresses**   ppEnumBegAddresses,
   IEnumDebugAddresses**   ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromContext(
   IDebugDocumentContext2  pDocContext,
   bool                    fStatmentOnly,
   out IEnumDebugAddresses ppEnumBegAddresses,
   out IEnumDebugAddresses ppEnumEndAddresses
);
```

## <a name="parameters"></a>매개 변수
`pDocContext`\
[in] 문서 컨텍스트입니다.

`fStatmentOnly`\
[in] TRUE 이면 단일 문으로 디버그 주소를 제한 합니다.

`ppEnumBegAddresses`\
[out] 이 문 또는 줄을 사용 하 여 연결 시작 디버그 주소에 대 한 열거자를 반환 합니다.

`ppEnumEndAddresses`\
[out] 반환 된 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) 관련 된이 문 또는 줄 끝 디버그 주소에 대 한 열거자입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 문서 컨텍스트는 일반적으로 다양 한 소스 줄을 나타냅니다. 이러한 줄을 사용 하 여 연결 된 마지막 디버그 주소 및이 메서드는 시작을 제공 합니다. 일부 언어 문을 여러 줄 또는 둘 이상의 문을 포함 하는 줄에 걸쳐 있을 수 있습니다. 이 메서드는 단일 문으로 디버그 주소를 제한 하는 플래그를 제공 합니다.

 템플릿의 경우와 같이 여러 디버그 주소 단일 문에 대 한 것 같습니다.

## <a name="see-also"></a>참고자료
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromPosition](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromposition.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)