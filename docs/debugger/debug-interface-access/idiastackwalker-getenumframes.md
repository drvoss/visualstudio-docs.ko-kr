---
title: 'IDiaStackWalker:: getEnumFrames | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd6f5219edf9426067a4431936caa2186604e1cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741547"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
X86 플랫폼용 스택 프레임 열거자를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>매개 변수
 `pHelper`

진행 도우미 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) 개체입니다.

 `ppEnum`

제한이 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) 개체의 목록을 포함 하는 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) 개체를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 다른 플랫폼에서 스택 프레임 목록을 가져오려면 [IDiaStackWalker:: getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)