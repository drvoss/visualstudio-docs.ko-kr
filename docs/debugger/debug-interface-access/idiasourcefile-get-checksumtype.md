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
ms.openlocfilehash: 35e5719d285e9e99e5f7429685fa04a2c6d7f3ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62832287"
---
# <a name="idiasourcefilegetchecksumtype"></a>IDiaSourceFile::get_checksumType
체크섬 유형을 검색합니다.

## <a name="syntax"></a>구문

```C++
HRESULT get_checksumType ( 
   DWORD* pRetVal
);
```

#### <a name="parameters"></a>매개 변수
 `pRetVal`

[out] 체크섬 형식을 반환합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.

## <a name="remarks"></a>설명
 체크섬 유형 체크섬 알고리즘에 매핑할 수 있는 값입니다. 예를 들어 표준 PDB 파일 형식 다음 값 중 하나가 있어야 일반적으로 수 있습니다.

|체크섬 유형|CryptoAPI 레이블|설명|
|-------------------|---------------------|-----------------|
|0|\<없음 >|체크섬 존재 합니다.|
|1|`CALG_MD5`|MD5 해시 알고리즘을 사용 하 여 생성 된 체크섬입니다.|
|2|`CALG_SHA1`|SHA1 해시 알고리즘을 사용 하 여 생성 된 체크섬입니다.|

 합니다 `CryptoAPI` 레이블은에서 `ALG_ID` 열거형입니다. 해시 알고리즘에 대 한 자세한 내용은 참조는 `CryptoAPI` Microsoft의 섹션 [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)]합니다.

 소스 파일에 대 한 실제 체크섬 바이트를 가져오려면 호출 합니다 [idiasourcefile:: Get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) 메서드.

## <a name="see-also"></a>참고 항목
- [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
- [IDiaSourceFile::get_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)