---
title: IDebugDocumentPosition2::GetRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c67828e2d9e1cb0c75d272b57e7c6b610a84fdd5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66326464"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
이 문서에 대 한 범위를 가져옵니다.

## <a name="syntax"></a>구문

```cpp
HRESULT GetRange( 
   TEXT_POSITION* pBegPosition,
   TEXT_POSITION* pEndPosition
);
```

```csharp
int GetRange( 
   TEXT_POSITION[] pBegPosition,
   TEXT_POSITION[] pEndPosition
);
```

## <a name="parameters"></a>매개 변수
`pBegPosition`\
[out에서] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조 시작 위치를 사용 하 여 입력 됩니다. 이 정보가 필요 하지 않은 경우이 인수를 null 값으로 설정 합니다.

`pEndPosition`\
[out에서] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) 구조 끝 위치를 사용 하 여 입력 됩니다. 이 정보가 필요 하지 않은 경우이 인수를 null 값으로 설정 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 위치 중단점에 대 한 문서 위치에 지정 된 범위는 실제로 코드를 적용 하는 문을 계속 해 서 검색할 디버그 엔진 (DE)에 의해 사용 됩니다. 예를 들어, 다음 코드를 고려하세요.

```
Line 5: // comment
Line 6: x = 1;
```

 줄 5에는 디버그 중인 프로그램 코드가 없는 기여 합니다. 다섯 번째 줄에 중단점을 설정 하는 디버거 코드를 적용 하는 첫 번째 줄의 일정량을 앞으로 검색 DE를 하려는 경우 디버거가 중단점 수 제대로 배치 하는 추가 후보 줄을 포함 하는 범위를 지정 합니다. DE 중단점을 수락할 수 있는 줄을 찾을 때까지 해당 줄을 통해 앞으로 검색 한 다음 됩니다.

## <a name="see-also"></a>참고자료
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)