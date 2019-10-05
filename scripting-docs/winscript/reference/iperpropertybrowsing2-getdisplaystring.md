---
title: IPerPropertyBrowsing2::GetDisplayString | Microsoft 문서
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f6f63db8d9c032b8e880f05d4d21e50fd56c74e2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944867"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
가져오기 본질적으로 볼 수 없는 형식을 반환 되는 텍스트를 표시 하는 문자열 속성을 설명 하는 이름 및 호출자의 사용자 인터페이스에 표시할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dispid`  
 [in] 표시 이름이 요청 된 속성의 식별자를 디스패치하십시오.  
  
 `pBstr`  
 [out] 에 대 한 포인터를 `BSTR` 으로 식별 된 속성에 대 한 표시 이름이 포함 된 `dispID`합니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 반환 `HRESULT`, 일반적으로 `S_OK`.  
  
## <a name="remarks"></a>설명  
 반환된 된 문자열 속성의 올바른 값이 아닙니다. 속성의 문자열 표시는 것입니다.  
  
## <a name="see-also"></a>참고 항목  
 [IPerPropertyBrowsing2 인터페이스 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)