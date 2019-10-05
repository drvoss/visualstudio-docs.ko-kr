---
title: 'Idiareadexeatoffsetcallback:: Readexecutableat | Microsoft Docs'
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
ms.openlocfilehash: 0f199db93fa2ea0b3ee2633f9af8a02fff5a4fdf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62828210"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
지정 된 실행 파일에서 지정된 된 오프셋에서 시작 하는 바이트 수를 읽습니다.

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

[in] 실행 파일 읽기를 시작할 오프셋입니다.

 cbData

[in] 읽을 바이트 수입니다.

 pcbData

[out] 읽은 바이트 수를 반환 합니다.

 data[]

[out에서] 파일에서 읽은 바이트를 사용 하 여 입력은 배열입니다.

## <a name="remarks"></a>설명
 이 메서드는 절대 파일 오프셋을 사용 하 여 실행 파일에서 데이터 바이트를 로드 하려면 DIA 지원 코드에서 호출 됩니다. 이 메서드를 지 원하는 호출을 [idiadatasource:: Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) 메서드.

## <a name="see-also"></a>참고 항목
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)