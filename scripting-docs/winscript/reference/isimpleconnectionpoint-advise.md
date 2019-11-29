---
title: 'ISimpleConnectionPoint:: Advise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Advise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Advise
ms.assetid: 59ded60d-b938-4110-aca3-e69ba234ca9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d7d08d4774dffbfd840c674b15abe82bedb37e5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571832"
---
# <a name="isimpleconnectionpointadvise"></a>ISimpleConnectionPoint::Advise
단순 연결 지점 개체와 클라이언트의 싱크 간에 연결을 설정 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Advise(  
   IDispatch*  pdisp,  
   DWORD*      pdwCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pdisp`  
 진행 클라이언트의 advise 싱크에 있는 `IDispatch` 인터페이스에 대 한 포인터입니다. 클라이언트의 싱크는 단순 연결 지점에서 나가는 호출을 받습니다.  
  
 `pdwCookie`  
 제한이 이 연결을 고유 하 게 식별 하는 반환 된 토큰에 대 한 포인터입니다. 호출자는 나중에이 토큰을 사용 하 여 연결을 `ISimpleConnectionPoint::Unadvise` 메서드에 전달 함으로써 삭제 합니다. 연결이 제대로 설정 되지 않은 경우이 값은 0입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 단순 연결 지점 개체와 클라이언트의 싱크 간에 연결을 설정 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [ISimpleConnectionPoint 인터페이스](../../winscript/reference/isimpleconnectionpoint-interface.md)   
 [ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)