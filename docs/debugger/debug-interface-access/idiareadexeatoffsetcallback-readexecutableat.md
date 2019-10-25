---
title: 'IDiaReadExeAtOffsetCallback:: ReadExecutableAt | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d913a229dafb64570728434576716ba396648af3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72742828"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
실행 파일에서 지정 된 오프셋부터 시작 하 여 지정 된 바이트 수를 읽습니다.

## <a name="syntax"></a>구문

```C++
HRESULT ReadExecutableAt ( 
   DWORDLONG fileOffset,
   DWORD     cbData,
   DWORD*    pcbData,
   BYTE      data[]
);
```

#### <a name="parameters"></a>매개 변수
 fileOffset

진행 읽기를 시작할 실행 파일의 오프셋입니다.

 cbData

진행 읽을 바이트 수입니다.

 pcbData

제한이 읽은 바이트 수를 반환 합니다.

 데이터[]

[in, out] 파일에서 읽은 바이트를 사용 하 여 채워진 배열입니다.

## <a name="remarks"></a>주의
 이 메서드는 절대 파일 오프셋을 사용 하 여 실행 파일에서 데이터 바이트를 로드 하기 위해 DIA 지원 코드에서 호출 됩니다. 이 메서드는 [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드를 지원 하기 위해 호출 됩니다.

## <a name="see-also"></a>참조
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)