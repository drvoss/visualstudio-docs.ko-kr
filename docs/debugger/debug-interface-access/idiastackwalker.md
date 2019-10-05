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
ms.openlocfilehash: 5ad74f92765ee449eab1e3089511a063e70d96a0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62831935"
---
# <a name="idiastackwalker"></a>IDiaStackWalker
스택 작업을 수행 하는 방법 설명 정보를 사용 하 여.pdb 파일에 제공 합니다.

## <a name="syntax"></a>구문

```
IDiaStackWalker: IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
다음 표에서의 메서드를 보여 줍니다. `IDiaStackWalker`합니다.

|메서드|설명|
|------------|-----------------|
|[IDiaStackWalker::getEnumFrames](../../debugger/debug-interface-access/idiastackwalker-getenumframes.md)|X86에 대 한 스택 프레임 열거자를 검색 플랫폼입니다.|
|[IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)|특정 플랫폼 형식에 대 한 스택 프레임 열거자를 검색합니다.|

## <a name="remarks"></a>설명
이 인터페이스는 로드 된 모듈에 대 한 스택 프레임의 목록을 가져오는 데 사용 됩니다. 메서드에 전달 되는 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) 스택 프레임 목록을 만드는 데 필요한 정보를 제공 하는 개체 (클라이언트 응용 프로그램에서 구현 됨).

## <a name="notes-for-callers"></a>호출자에 대 한 정보
이 인터페이스를 호출 하 여 가져온 합니다 `CoCreateInstance` 클래스 식별자를 사용 하 여 메서드 `CLSID_DiaStackWalker` 와의 인터페이스 ID `IID_IDiaStackWalker`합니다. 이 인터페이스는 가져오는 방법을 보여 줍니다.

## <a name="example"></a>예제
가져오는 방법을 보여 주는이 예제는 `IDiaStackWalker` 인터페이스입니다.

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
헤더: Dia2.h

라이브러리: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>참고 항목
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
