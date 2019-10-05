---
title: 'Idialoadcallback:: Notifyopenpdb | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback::NotifyOpenPDB method
ms.assetid: c0547f99-8468-4e57-82ca-9ef7d6707c8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5945ba54f1c09f4f13d2a982e90a3bb58cfb5f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62839760"
---
# <a name="idialoadcallbacknotifyopenpdb"></a>IDiaLoadCallback::NotifyOpenPDB
후보.pdb 파일을 열 때 호출 됩니다.

## <a name="syntax"></a>구문

```C++
HRESULT NotifyOpenPDB ( 
   LPCOLESTR pdbPath,
   HRESULT   resultCode
);
```

#### <a name="parameters"></a>매개 변수
 `pdbPath`

[in] .Pdb 파일의 전체 경로입니다.

 `resultCode`

[in] 성공 여부를 나타내는 코드입니다 (`S_OK`) 또는이 파일에 적용 될 때 로드 실패 합니다.

## <a name="return-value"></a>반환 값
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 반환 코드는 일반적으로 무시 됩니다.

## <a name="see-also"></a>참고 항목
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)