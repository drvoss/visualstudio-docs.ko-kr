---
title: 'ISimpleConnectionPoint:: Unadvise | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ISimpleConnectionPoint.Unadvise
apilocation:
- pdm.dll
helpviewer_keywords:
- ISimpleConnectionPoint::Unadvise
ms.assetid: eae06a58-ed42-4839-aad4-14420b15343f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e00c172fd33eb0ccf27aaf28e0e2f692c1a353ab
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571756"
---
# <a name="isimpleconnectionpointunadvise"></a>ISimpleConnectionPoint::Unadvise
@No__t_0를 통해 이전에 설정 된 advise 연결을 종료 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Unadvise(  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwCookie`  
 진행 @No__t_0에서 반환 되는 종료할 연결의 토큰입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 Advise 연결이 종료 되 면 연결 지점은 `ISimpleConnectionPoint::Advise` 메서드 중 연결에 대해 저장 된 포인터의 `Release` 메서드를 호출 합니다. 이 호출은 연결 지점에서 advise 싱크 `QueryInterface`를 호출할 때 `ISimpleConnectionPoint::Advise` 중에 수행 된 `AddRef`를 반대로 바꿉니다.  
  
## <a name="see-also"></a>참조  
 [ISimpleConnectionPoint 인터페이스](../../winscript/reference/isimpleconnectionpoint-interface.md)