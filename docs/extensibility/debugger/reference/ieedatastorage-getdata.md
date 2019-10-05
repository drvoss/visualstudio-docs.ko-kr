---
title: IEEDataStorage::GetData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8859b019559f21797e23fa9a568b0ad7d649454
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319643"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
개체에서 지정 된 바이트 수를 검색합니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetData(
   ULONG  dataSize,
   ULONG* sizeGotten,
   BYTE*  data
);
```

```csharp
int GetData(
   uint     dataSize,
   out uint sizeGotten,
   byte[]   data
);
```

## <a name="parameters"></a>매개 변수
`dataSize`\
[in] 검색할 바이트 수 (의 `data` 배열 최소 바이트이 수가이 보유 해야 합니다).

`sizeGotten`\
[out] 실제로 검색 하는 바이트 수를 반환 합니다.

`data`\
[out에서] 요청한 데이터를로 채워질 배열입니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 권장 되는이 방법 사용 검색 프로세스에서 바이트를 건너뛸 수 없기 때문 로컬 배열로 모든 데이터 바이트를 검색 하는 것입니다. 이 예에서 매개 변수 `dataSize` 값에서 반환 해야 합니다 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) 메서드.

## <a name="see-also"></a>참고자료
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)