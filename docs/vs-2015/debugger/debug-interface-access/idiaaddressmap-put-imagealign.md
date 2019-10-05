---
title: 'Idiaaddressmap:: Put_imagealign | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e0fa57c38c8451bde84d96ab32bc7980c5e2d8b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442216"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이미지 맞춤을 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 NewVal  
 [in] 실행 파일에 대 한 새 이미지 맞춤 값입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다.  
  
## <a name="remarks"></a>설명  
 이미지 (로드 된 실행 파일)는 지정 된 메모리 경계에 정렬 됩니다. 현재 시스템 아키텍처 및 시간 옵션을 컴파일 및 링크 하 여이 맞춤을 달라질 수 있습니다. 이미지 맞춤 바이트 경계 항상 켜져 있습니다. 다음 이미지 맞춤 값이 유효한 지: 1, 2, 4, 8, 16, 32, 64 바이트 경계입니다.  
  
 현재 이미지 맞춤을 호출 하 여 검색할 수는 [idiaaddressmap:: Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) 메서드.  
  
> [!NOTE]
> 이미지는이 메서드를 호출할 수에 의해 이미 로드 되었습니다. `put_imageAlign` 메서드는 새 맞춤이 필요 하 고 이미지 이동 되거나 변경 된 경우에 일반적으로 사용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
