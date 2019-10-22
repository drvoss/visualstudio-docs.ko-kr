---
title: 'IPerPropertyBrowsing2:: GetPredefinedStrings | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetPredefinedStrings
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetPredefinedStrings
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 55ade724dd9ee5d59feb9d04c5b525ca839a9cec
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576767"
---
# <a name="iperpropertybrowsing2getpredefinedstrings"></a>IPerPropertyBrowsing2::GetPredefinedStrings
호출자가이 속성의 가능한 값을 나타내는 문자열 포인터의 계산 된 배열로 목록 상자를 채울 수 있도록 허용 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dispid`  
 진행 호출자가 문자열 목록을 요청 하는 속성의 디스패치 식별자입니다.  
  
 `pCaStrings`  
 제한이 메서드 할당 문자열 포인터 배열의 요소 수와 주소를 포함 하는, 호출자가 할당 한 계산 된 배열 구조에 대 한 포인터입니다. 메서드가 실패 하면 메모리가 할당 되지 않으며 구조체의 내용이 정의 되지 않습니다.  
  
 `pCaCookies`  
 제한이 메서드 할당 된 Dword 배열의 요소 수와 주소를 포함 하는, 호출자가 할당 한 계산 된 배열 구조에 대 한 포인터입니다. 메서드가 실패 하면 메모리가 할당 되지 않으며 구조체의 내용이 정의 되지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT` (일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IPerPropertyBrowsing2 인터페이스 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)