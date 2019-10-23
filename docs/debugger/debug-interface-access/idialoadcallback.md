---
title: IDiaLoadCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback interface
ms.assetid: 2f18c64c-2cf0-43fc-a447-21e82702ca2a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ca58a206fec15bb8a9ae7f68a278a4530be47d8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743034"
---
# <a name="idialoadcallback"></a>IDiaLoadCallback
DIA 기호 찾기 프로시저에서 콜백을 수신 하므로 사용자 인터페이스를 사용 하 여 위치 시도의 진행 상황을 보고할 수 있습니다.

## <a name="syntax"></a>구문

```
IDiaLoadCallback : IUnknown
```

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드
 이 인터페이스에 의해 노출 되는 메서드는 다음과 같습니다.

|메서드|설명|
|------------|-----------------|
|[IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)|.Exe 파일에서 디버그 디렉터리가 발견 될 때 호출 됩니다.|
|[IDiaLoadCallback::NotifyOpenDBG](../../debugger/debug-interface-access/idialoadcallback-notifyopendbg.md)|지망자 파일이 열려 있을 때 호출 됩니다.|
|[IDiaLoadCallback::NotifyOpenPDB](../../debugger/debug-interface-access/idialoadcallback-notifyopenpdb.md)|후보 .pdb 파일이 열려 있을 때 호출 됩니다.|
|[IDiaLoadCallback::RestrictRegistryAccess](../../debugger/debug-interface-access/idialoadcallback-restrictregistryaccess.md)|레지스트리 쿼리를 사용 하 여 기호 검색 경로를 찾을 수 있는지 여부를 결정 합니다.|
|[IDiaLoadCallback::RestrictSymbolServerAccess](../../debugger/debug-interface-access/idialoadcallback-restrictsymbolserveraccess.md)|기호를 확인 하기 위해 기호 서버에 대 한 액세스가 허용 되는지 여부를 결정 합니다.|

## <a name="remarks"></a>주의
 클라이언트 응용 프로그램은이 인터페이스를 구현 하 고 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드에 대 한 호출에서이 인터페이스에 대 한 참조를 제공 합니다.

 로드 프로세스에 적용 될 수 있는 추가 제한 사항은 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md) 인터페이스를 참조 하세요.

## <a name="requirements"></a>요구 사항
 헤더: Dia2

 라이브러리: diaguids

 DLL: msdia80

## <a name="see-also"></a>참조
- [인터페이스(디버그 인터페이스 액세스 SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)