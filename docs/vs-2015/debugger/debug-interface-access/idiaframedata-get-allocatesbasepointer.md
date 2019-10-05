---
title: 'Idiaframedata:: Get_allocatesbasepointer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 90a32930c51caad61e07b0e6fdfe5b164a5515bf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203664"
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 주소 범위에서 코드에 대 한 기본 포인터 할당 되었는지 여부를 나타내는 플래그를 검색 합니다. 이 메서드는 사용 되지 않습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 [out] 반환 `TRUE` 기본 포인터 할당 되어 있습니다; 그렇지 않으면 반환 `FALSE`합니다.  
  
## <a name="return-value"></a>반환 값  
 성공하면 `S_OK`를 반환합니다. 반환 `S_FALSE` 경우이 속성이 지원 되지 않습니다. 그러지 않으면 오류 코드가 반환됩니다.  
  
## <a name="remarks"></a>설명  
 FPO_DATA, 이전의 액세스는 또는 프로그램 문자열을 반환 하는 경우 코드 에서만이 속성을 사용 해야 합니다 [idiaframedata:: Get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) 메서드는 `NULL`합니다. 그렇지 않은 경우 프로그램 문자열이 이전 레지스터 값을 계산 하는 데 필요한 모든 정보를 포함 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
