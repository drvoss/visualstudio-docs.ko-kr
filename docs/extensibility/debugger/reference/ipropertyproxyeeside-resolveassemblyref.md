---
title: IPropertyProxyEESide::ResolveAssemblyRef | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3d2fd21b39e171238319c857ad0384db1d7635d7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66353455"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
지정 된 관리 되는 어셈블리 참조의 위치를 결정합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT ResolveAssemblyRef(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  assemLocation,
   ASSEMBLYLOCRESOLUTION* alr
);
```

```csharp
int ResolveAssemblyRef(
   ref string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     assemLocation,
   out enum_ASSEMBLYLOCRESOLUTION alr
);
```

## <a name="parameters"></a>매개 변수
`assemName`\
[in] 확인할 어셈블리의 이름입니다.

`assemBytes`\
[out] 반환 된 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) 참조와 연결 된 어셈블리 바이트를 포함 하는 개체입니다.

`assemPdb`\
[out] 반환 된 `IEEDataStorage` 이 참조와 연결 된 데이터를 저장 하는 기호를 포함 하는 개체입니다.

`assemLocation`\
[out] 이 참조의 경로 위치를 반환합니다.

`alr`\
[out] 값을 반환 합니다 [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) 이 참조의이 어셈블리의 위치를 나타내는 열거형입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 이 메서드는 사용자 지정 식 계산기에서 일반적으로 구현 되지 않았습니다.

## <a name="see-also"></a>참고자료
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)