---
title: 'ICanHandleException:: CanHandleException | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ICanHandleException.CanHandleException
apilocation:
- scrobj.dll
helpviewer_keywords:
- ICanHandleException::CanHandleException
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c536d35dcb9f0faca8b033ecd39aec520a2e260a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575717"
---
# <a name="icanhandleexceptioncanhandleexception"></a>ICanHandleException::CanHandleException
스크립트 엔진의 호출자가 지정 된 예외를 처리할 수 있는지 여부를 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pExcepInfo`  
 진행 예외 처리기를 찾을 수 없는 경우 보고 될 정보를 포함 하는 `EXCEPINFO` 구조체에 대 한 포인터입니다.  
  
 `pvar`  
 진행 `throw` 문에서 throw 되는 값과 같은 예외와 관련 된 값입니다. 이 매개 변수는 `NULL`일 수 있습니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|호출자가 예외를 처리할 수 있습니다.|  
|`E_FAIL`|호출자가 예외를 처리할 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 `IDispatchEx::InvokeEx`또는 유사한 메서드를 호출 하면 예외가 발생 하 고 스크립트 엔진은 `ICanHandleException` 인터페이스를 지 원하는 스크립트의 호출자 체인에서 호출자를 확인 하 여 예외를 처리할 수 있음을 나타냅니다. 호출자가 예외를 처리할 수 없는 경우 스크립트 엔진이 중단 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Icanhandleexception 인터페이스](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)