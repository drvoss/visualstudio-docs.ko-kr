---
title: 'IPerPropertyBrowsing2:: GetDisplayString | Microsoft Docs'
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
ms.openlocfilehash: bc702ad15d1aba04bf991c04b585728afde4fb41
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571459"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
기본적으로 볼 수 없는 형식을 표시 하는 문자열을 가져옵니다. 반환 된 텍스트는 속성을 설명 하는 이름이 며 호출자의 사용자 인터페이스에 표시 될 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dispid`  
 진행 표시 이름이 요청 된 속성의 디스패치 식별자입니다.  
  
 `pBstr`  
 제한이 @No__t_1에 의해 식별 되는 속성의 표시 이름을 포함 하는 `BSTR`에 대 한 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
 유효한 `HRESULT` (일반적으로 `S_OK`)를 반환 합니다.  
  
## <a name="remarks"></a>주의  
 반환 된 문자열이 속성의 올바른 값이 아닙니다. 단지 속성의 문자열 표시입니다.  
  
## <a name="see-also"></a>참조  
 [IPerPropertyBrowsing2 인터페이스 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)