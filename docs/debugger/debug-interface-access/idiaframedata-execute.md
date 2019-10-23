---
title: IDiaFrameData::execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88c9af8293dfc6a35e5f0e42d9596494d74b10aa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743692"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
스택 해제를 수행 하 고 스택 워크 프레임 인터페이스에서 결과를 반환 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>매개 변수
 `frame`

진행 프레임 레지스터의 상태를 보유 하는 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) 개체입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다. 다음 표에서는이 메서드에 사용할 수 있는 반환 값을 보여 줍니다.

|값|설명|
|-----------|-----------------|
|E_DIA_INPROLOG|프롤로그 코드에서는 스택 프레임을 실행할 수 없습니다.|
|E_DIA_SYNTAX|프레임 프로그램에서 구문 분석 오류가 발생 했습니다.|
|E_DIA_FRAME_ACCESS|레지스터 또는 메모리에 액세스할 수 없습니다.|
|E_DIA_VALUE|값 계산에 오류가 있습니다 (예: 0으로 나누기).|

## <a name="remarks"></a>주의
 이 메서드는 디버깅 하는 동안 호출 되어 스택을 해제 합니다. [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) 개체는 레지스터 업데이트를 수신 하 고 `execute` 메서드에서 사용 하는 메서드를 제공 하기 위해 클라이언트 응용 프로그램에 의해 구현 됩니다.

## <a name="see-also"></a>참조
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)