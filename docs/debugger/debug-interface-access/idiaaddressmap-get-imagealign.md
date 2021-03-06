---
title: 'Idiaaddressmap:: Get_imagealign | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::get_imageAlign method
ms.assetid: f1ba8071-669c-4cf7-9ac0-02f26d99f366
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 409b33953d6674066eff9570288de2e3912bdab3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908852"
---
# <a name="idiaaddressmapgetimagealign"></a>IDiaAddressMap::get_imageAlign
현재 이미지 맞춤을 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```C++  
HRESULT get_imageAlign (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 [out] 실행 파일에서 이미지 맞춤 값을 반환합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이미지는 이미지를 로드 및 생성 하는 방법에 따라 특정 메모리 경계에 정렬 됩니다. 맞춤은 일반적으로 1, 2, 4, 8, 16, 32 또는 64 바이트 경계입니다. 이미지 맞춤을 호출 하 여 설정할 수 있습니다 합니다 [idiaaddressmap:: Put_imagealign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md) 메서드.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::put_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-put-imagealign.md)