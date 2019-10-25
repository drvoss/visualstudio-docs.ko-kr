---
title: IDiaStackWalker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker interface
ms.assetid: 4a61a22a-9cf8-4ea1-9e6e-b42f96872d40
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2366c933bf072c295b29d06ff5610bd3735c0077
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741516"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
.Pdb 파일의 정보를 사용 하 여 스택 워크를 수행 하는 메서드를 제공 합니다.

## <a name="syntax"></a>구문

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서는 `IDiaStackWalker`의 메서드를 보여 줍니다.

|메서드|설명|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|X86 플랫폼용 스택 프레임 열거자를 검색 합니다.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|특정 플랫폼 형식에 대 한 스택 프레임 열거자를 검색 합니다.|

## <a name="remarks"></a>주의
이 인터페이스는 로드 된 모듈의 스택 프레임 목록을 가져오는 데 사용 됩니다. 각 메서드는 스택 프레임 목록을 만드는 데 필요한 정보를 제공 하는 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) 개체 (클라이언트 응용 프로그램에서 구현 됨)에 전달 됩니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
이 인터페이스는 클래스 식별자 `CLSID_DiaStackWalker`와 `IID_IDiaStackWalker`의 인터페이스 ID를 사용 하 여 `CoCreateInstance` 메서드를 호출 하 여 가져옵니다. 이 예제에서는이 인터페이스를 가져오는 방법을 보여 줍니다.

## <a name="example"></a>예제
이 예제에서는 `IDiaStackWalker` 인터페이스를 가져오는 방법을 보여 줍니다.

```C++

IDiaStackWalker* pStackWalker;
HRESULT hr = CoCreateInstance(CLSID_DiaStackWalker,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaStackWalker,
                              (void**) &pStackWalker);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>요구 사항
헤더: Dia2

라이브러리: diaguids

DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
