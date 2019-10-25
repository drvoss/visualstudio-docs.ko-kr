---
title: IDiaReadExeAtRVACallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback interface
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2aee44ff3acc1d7423e19de8fd64be0e46d8e372
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742801"
---
# <a name="idiareadexeatrvacallback"></a>IDiaReadExeAtRVACallback
클라이언트 응용 프로그램에서 상대 가상 주소에 지정 된 대로 실행 파일의 바이트를 제공할 수 있도록 합니다.

## <a name="syntax"></a>구문

```
IDiaReadExeAtRVACallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 다음 표에서는 `IDiaReadExeAtRVACallback`의 메서드를 보여 줍니다.

|메서드|설명|
|------------|-----------------|
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|실행 파일에서 지정 된 RVA (상대 가상 주소)에서 시작 하 여 지정 된 바이트 수를 읽습니다.|

## <a name="remarks"></a>주의
 클라이언트 응용 프로그램은 상대 가상 주소를 사용 하는 실행 파일의 바이트를 실행 파일의 파일에 제공 하기 위해이 인터페이스를 구현 합니다. 절대 파일 오프셋을 사용 하려면 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) 인터페이스를 구현 합니다.

## <a name="notes-for-callers"></a>호출자 참고 사항
 이 메서드는 클라이언트 응용 프로그램에서 구현 되 고 파일을 읽기 위한 대체 메서드로 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드에 전달 됩니다.

## <a name="requirements"></a>요구 사항
 헤더: Dia2

 라이브러리: diaguids

 DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)