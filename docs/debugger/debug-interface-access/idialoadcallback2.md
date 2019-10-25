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
ms.openlocfilehash: 7db8b6a115acdafeca2e7e0adbe11be97834cd6d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742955"
---
# <a name="idialoadcallback2"></a>IDiaLoadCallback2
DIA 기호 찾기 프로시저에서 콜백을 수신 하 여 찾기 프로세스에 제한이 적용 될 수 있도록 합니다.

## <a name="syntax"></a>구문

```
IDiaLoadCallback2 : IDiaLoadCallback
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) 인터페이스의 메서드 외에도이 인터페이스는 다음 메서드를 노출 합니다.

|메서드|설명|
|------------|-----------------|
|[IDiaLoadCallback2::RestrictOriginalPathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictoriginalpathaccess.md)|원본 디버그 디렉터리에서 .pdb 파일을 찾을 지 여부를 결정 합니다.|
|[IDiaLoadCallback2::RestrictReferencePathAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictreferencepathaccess.md)|.Exe 파일이 있는 경로에서 .pdb 파일을 찾을 수 있는지 여부를 확인 합니다.|
|[IDiaLoadCallback2::RestrictDBGAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictdbgaccess.md)|Dbg 파일에서 디버그 정보를 찾을 수 있는지 여부를 확인 합니다.|
|[IDiaLoadCallback2::RestrictSystemRootAccess](../../debugger/debug-interface-access/idialoadcallback2-restrictsystemrootaccess.md)|시스템 루트 디렉터리에서 .pdb 파일을 검색할 수 있는지 여부를 확인 합니다.|

## <a name="remarks"></a>주의
 클라이언트 응용 프로그램은이 인터페이스를 구현 하 고 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드에 대 한 호출에서이 인터페이스에 대 한 참조를 제공 합니다. [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md) 인터페이스의 모든 메서드를 구현 해야 합니다.

## <a name="requirements"></a>요구 사항
 헤더: Dia2

 라이브러리: diaguids

 DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)