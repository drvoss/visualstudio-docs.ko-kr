---
title: IDiaSourceFile::get_checksum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f4367a7862dabe248dfbe08e64c45598abe3679
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741841"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
체크섬 바이트를 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_checksum ( 
   DWORD  cbData,
   DWORD* pcbData,
   BYTE   data[]
);
```

#### <a name="parameters"></a>매개 변수
 `cbData`

진행 데이터 버퍼의 크기 (바이트)입니다.

 `pcbData`

제한이 체크섬 바이트의 수를 반환 합니다. 이 매개 변수를 `NULL` 수 없습니다.

 `data`

[in, out] 체크섬 바이트로 채워지는 버퍼입니다. 이 매개 변수를 `NULL` 하면 `pcbData`는 필요한 바이트 수를 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 체크섬 바이트를 생성 하는 데 사용 된 체크섬 알고리즘의 유형을 확인 하려면 [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) 메서드를 호출 합니다.

 체크섬은 일반적으로 소스 파일의 이미지에서 생성 되므로 소스 파일의 변경 내용이 체크섬 바이트의 변경 내용에 반영 됩니다. 체크섬 바이트가 파일의 로드 된 이미지에서 생성 된 체크섬과 일치 하지 않으면 파일이 손상 되거나 변조 된 것으로 간주 됩니다.

 일반적인 체크섬의 크기는 32 바이트이 하 이지만이 체크섬의 최대 크기인 것으로 가정 하지는 않습니다. @No__t_0 매개 변수를 `NULL`으로 설정 하 여 체크섬을 검색 하는 데 필요한 바이트 수를 가져옵니다. 그런 다음 적절 한 크기의 버퍼를 할당 하 고 새 버퍼를 사용 하 여이 메서드를 한 번 더 호출 합니다.

## <a name="see-also"></a>참조
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)