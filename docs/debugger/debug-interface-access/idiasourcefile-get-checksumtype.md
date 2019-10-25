---
title: IDiaSourceFile::get_checksumType | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksumType method
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c85c6ce8f03534c3ed810e530dbd12d8c6d115be
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741826"
---
# <a name="idiasourcefileget_checksumtype"></a>IDiaSourceFile::get_checksumType
체크섬 형식을 검색 합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_checksumType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

제한이 체크섬 유형을 반환 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 `S_OK`을 반환 합니다. 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>주의
 체크섬 유형은 체크섬 알고리즘에 매핑될 수 있는 값입니다. 예를 들어 표준 PDB 파일 형식은 일반적으로 다음 값 중 하나를 사용할 수 있습니다.

|체크섬 형식|CryptoAPI 레이블|설명|
|-------------------|---------------------|-----------------|
|0|\<none >|체크섬이 없습니다.|
|1|`CALG_MD5`|MD5 해시 알고리즘을 사용 하 여 생성 된 체크섬입니다.|
|2|`CALG_SHA1`|SHA1 해시 알고리즘을 사용 하 여 생성 된 체크섬입니다.|

 @No__t_0 레이블은 `ALG_ID` 열거형에서 가져온 것입니다. 해시 알고리즘에 대 한 자세한 내용은 Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)]의 `CryptoAPI` 섹션을 참조 하세요.

 소스 파일에 대 한 실제 체크섬 바이트를 가져오려면 [IDiaSourceFile:: get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) 메서드를 호출 합니다.

## <a name="see-also"></a>참조
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)