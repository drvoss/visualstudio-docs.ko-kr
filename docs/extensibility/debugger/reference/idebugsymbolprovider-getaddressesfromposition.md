---
title: IDebugSymbolProvider::GetAddressesFromPosition | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition
helpviewer_keywords:
- IDebugSymbolProvider::GetAddressesFromPosition method
ms.assetid: 1b0f02cb-8ace-4614-88f3-0e10239012b3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dcaef1e9675ae395826865604833fdb6683df944
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310178"
---
# <a name="idebugsymbolprovidergetaddressesfromposition"></a>IDebugSymbolProvider::GetAddressesFromPosition
이 메서드는 디버그 주소의 배열에 문서 위치를 매핑합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetAddressesFromPosition( 
   IDebugDocumentPosition2* pDocPos,
   BOOL                     fStatmentOnly,
   IEnumDebugAddresses**    ppEnumBegAddresses,
   IEnumDebugAddresses**    ppEnumEndAddresses
);
```

```csharp
int GetAddressesFromPosition( 
   IDebugDocumentPosition2  pDocPos,
   bool                     fStatmentOnly,
   out IEnumDebugAddresses  ppEnumBegAddresses,
   out IEnumDebugAddresses  ppEnumEndAddresses
);
```

## <a name="parameters"></a>매개 변수
`pDocPos`\
[in] 문서 위치입니다.

`fStatmentOnly`\
[in] TRUE 이면 단일 문으로 디버그 주소를 제한 합니다.

`ppEnumBegAddresses`\
[out] 이 문 또는 줄을 사용 하 여 연결 시작 디버그 주소에 대 한 열거자를 반환 합니다.

`ppEnumEndAddresses`\
[out] 반환 된 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) 관련 된이 문 또는 줄 끝 디버그 주소에 대 한 열거자입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 문서 위치는 일반적으로 다양 한 소스 줄을 나타냅니다. 이러한 줄을 사용 하 여 연결 된 마지막 디버그 주소 및이 메서드는 시작을 제공 합니다. 일부 언어 문을 여러 줄 또는 둘 이상의 문을 포함 하는 줄에 걸쳐 있을 수 있습니다. 이 메서드는 단일 문으로 디버그 주소를 제한 하는 플래그를 제공 합니다.

 템플릿의 경우와 같이 여러 디버그 주소 단일 문에 대 한 것 같습니다.

## <a name="see-also"></a>참고자료
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)