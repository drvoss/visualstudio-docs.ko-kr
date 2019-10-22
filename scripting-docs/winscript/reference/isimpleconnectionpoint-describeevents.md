---
title: ISimpleConnectionPoint::D escribeEvents | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.DescribeEvents
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::DescribeEvents
ms.assetid: 659ea05f-d41e-424a-bb38-df7672b2d135
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5000689d588fe3f63ec5408893187bba8d13d63
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571812"
---
# <a name="isimpleconnectionpointdescribeevents"></a>ISimpleConnectionPoint::DescribeEvents
지정 된 이벤트 범위에서 각 이벤트에 대 한 DISPID 및 이름을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT DescribeEvents(  
   ULONG    iEvent,  
   ULONG    cEvents,  
   DISPID*  prgid,  
   BSTR*    prgbstr,  
   ULONG*   pcEventsFetched  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `iEvent`  
 진행 검색할 첫 번째 이벤트의 인덱스입니다.  
  
 `cEvents`  
 진행 검색할 이벤트의 수입니다.  
  
 `prgid`  
 제한이 이벤트 DISPID 값의 배열입니다.  
  
 `prgbstr`  
 제한이 이벤트 이름 배열입니다.  
  
 `pcEventsFetched`  
 제한이 가져온 실제 이벤트 수입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`S_FALSE`|사용 가능한 것 보다 더 많은 이벤트가 요청 되었습니다. 사용할 수 없는 이벤트는 DISPID_NULL 및 NULL BSTR로 표시 됩니다.|  
|`E_INVALIDARG`|요소를 인출할 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 지정 된 이벤트 범위에서 각 이벤트에 대 한 DISPID와 이름을 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [ISimpleConnectionPoint 인터페이스](../../winscript/reference/isimpleconnectionpoint-interface.md)