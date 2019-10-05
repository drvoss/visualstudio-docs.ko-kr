---
title: IDiaLoadCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2 interface
ms.assetid: 9a44277d-cbed-4811-9bad-5a2aa0f09323
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: daf0b48aca06b404824059030052223a8545a6b0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839708"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
콜백 프로시저 찾기, 찾기 프로세스에 적용할 제한 수 있도록 DIA 기호에서 받습니다.

## <a name="syntax"></a>구문

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 메서드 외에도 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) 인터페이스에서이 인터페이스는 다음 메서드를 표시 합니다.

|메서드|설명|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|원래 디버그 디렉터리에.pdb 파일을 찾는 경우를 결정 합니다.|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|.Pdb 파일을 찾는.exe 파일이 위치한 경로에 허용 되는지 여부를 결정 합니다.|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|.Dbg 파일에서 디버그 정보를 찾고 허용 되는지 여부를 결정 합니다.|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|시스템 루트 디렉터리에.pdb 파일을 검색할 허용 되는지 여부를 결정 합니다.|

## <a name="remarks"></a>설명
 클라이언트 응용 프로그램이이 인터페이스를 구현 및 호출에 대 한 참조를 제공 합니다 [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드. 모든 메서드를 구현 해야 합니다 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) 인터페이스에도 합니다.

## <a name="requirements"></a>요구 사항
 헤더: Dia2.h

 라이브러리: diaguids.lib

 DLL: msdia80.dll

## <a name="see-also"></a>참고 항목
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)