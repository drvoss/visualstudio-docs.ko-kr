---
title: IPerPropertyBrowsing2 인터페이스 1 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2 interface
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 156cf9a1e104b8a2d7ffe4e48bd39642ef1abbd0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62944897"
---
# <a name="iperpropertybrowsing2-interface-1"></a>IPerPropertyBrowsing2 인터페이스 1
액세스 속성 페이지의 정보에서 제공 하는 개체입니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|`GetDisplayString`|지정된 된 속성을 설명 하는 텍스트 문자열을 반환 합니다.|  
|`MapPropertyToPage`|지정된 된 속성의 조작할 수 있는 속성 페이지의 CLSID를 반환 합니다.|  
|`GetPredefinedStrings`|계산된 된 문자열 배열을 반환 합니다 (`LPOLESTR` 포인터) 지정된 된 속성을 받아들일 수 있는 허용 되는 값의 설명을 나열 합니다.|  
|`SetPredefinedValue`|토큰에 의해 식별 되는 미리 정의 된 값을 속성의 값을 설정 합니다. `dwCookie.`|  
  
## <a name="requirements"></a>요구 사항  
 헤더: dbgprop.h