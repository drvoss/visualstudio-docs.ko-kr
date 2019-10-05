---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d874a00c3c82108c224f18922f2b4853279beaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322211"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
사용자 지정 특성의 이름이 지정 된 사용자 지정 특성 (바이트)를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>매개 변수
`pszCustomAttributeName`\
[in] 검색할 사용자 지정 특성의 이름을 포함 하는 문자열입니다.

`ppBlob`\
[out에서] 사용자 지정 특성 (바이트)를 사용 하 여 입력은 배열입니다.

`pdwLen`\
[out에서] 반환할 바이트의 최대 수를 지정 된 `ppBlob` 배열 및 배열에 실제로 기록 된 바이트 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 S_OK를 반환 하거나 사용자 지정 특성이 없으면 S_FALSE를 반환 합니다. 그러지 않으면 오류 코드가 반환됩니다.

## <a name="remarks"></a>설명
 설정 된 `ppBlob` 매개 변수 개수를 반환 하려면 null 값에 사용할 수 있는 바이트 특성입니다. 그런 다음 배열을 할당 하 고 해당 배열에 전달 된 `ppBlob` 매개 변수입니다.

 특성 바이트는 사용자 지정 특성의 원시 데이터를 나타냅니다.

 경우는 `ppBlob` 고 `pdwLen` 매개 변수가 null 값으로 설정, 사용자 지정 특성 단순히 있는지 확인 하기 위해이 메서드를 사용할 수 있습니다. 쉬운 대 안으로 것 인데, 호출 하 여 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) 메서드.

## <a name="see-also"></a>참고자료
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)