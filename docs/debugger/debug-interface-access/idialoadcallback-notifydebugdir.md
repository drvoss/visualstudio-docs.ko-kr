---
title: 'IDiaLoadCallback:: NotifyDebugDir | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyDebugDir method
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6618440cab9b9042ec371383f6c809ca1d0d11f7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72743083"
---
# <a name="idialoadcallbacknotifydebugdir"></a>IDiaLoadCallback::NotifyDebugDir
.Exe 파일에서 디버그 디렉터리가 발견 될 때 호출 됩니다.

## <a name="syntax"></a>구문

```C++
HRESULT NotifyDebugDir ( 
   BOOL  fExecutable,
   DWORD cbData,
   BYTE  data[]
);
```

#### <a name="parameters"></a>매개 변수
 `fExecutable`

[in] 디버그 디렉터리를 실행 파일 (dbg 파일 대신)에서 읽을 경우 `TRUE` 합니다.

 `cbData`

진행 디버그 디렉터리의 데이터 바이트 수입니다.

 `data[]`

진행 디버그 디렉터리로 채워진 배열입니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다. 반환 코드는 일반적으로 무시 됩니다.

## <a name="remarks"></a>주의
 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드는 실행 파일을 처리 하는 동안 디버그 디렉터리를 찾을 때이 콜백을 호출 합니다.

 이 메서드는 pdb 파일에서 찾을 수 없는 디버그 정보를 지원 하기 위해 클라이언트에서 실행 파일 및/또는 디버그 파일을 리버스 엔지니어링 하지 않아도 됩니다. 클라이언트는이 데이터를 사용 하 여 사용할 수 있는 디버그 정보 형식 및 실행 파일이 나 dbg 파일에 있는지 여부를 인식할 수 있습니다.

 기호를 제공 하는 데 필요한 경우 `IDiaDataSource::loadDataForExe` 메서드가 .pdb와 dbg 파일을 모두 투명 하 게 열기 때문에 대부분의 클라이언트에는이 콜백이 필요 하지 않습니다.

## <a name="see-also"></a>참조
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)