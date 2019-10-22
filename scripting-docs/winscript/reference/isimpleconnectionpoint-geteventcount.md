---
title: 'ISimpleConnectionPoint:: GetEventCount | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.GetEventCount
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::GetEventCount
ms.assetid: f1527d5b-6076-4536-8e59-e55da741ef39
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cfa392a052d415cef4c19f07c6c8e73704dfa45
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571810"
---
# <a name="isimpleconnectionpointgeteventcount"></a>ISimpleConnectionPoint::GetEventCount
이 인터페이스에 노출 되는 이벤트 수를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetEventCount(  
   ULONG*  pulCount  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pulCount`  
 제한이 이 인터페이스 수에 노출 되는 이벤트 수입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는이 인터페이스에 노출 되는 이벤트 수를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [ISimpleConnectionPoint 인터페이스](../../winscript/reference/isimpleconnectionpoint-interface.md)