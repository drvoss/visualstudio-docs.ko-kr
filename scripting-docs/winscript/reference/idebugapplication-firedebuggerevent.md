---
title: 'IDebugApplication:: FireDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.FireDebuggerEvent
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::FireDebuggerEvent
ms.assetid: fd1f602e-fc15-4158-a6e7-497ff5b4a509
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 00d895ed484e37f0ba38636a409876156ed97287
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575003"
---
# <a name="idebugapplicationfiredebuggerevent"></a>IDebugApplication::FireDebuggerEvent
디버거의 `IApplicationDebugger` 인터페이스에 대 한 일반 이벤트를 발생 시킵니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT FireDebuggerEvent(  
   REFGUID    riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `riid`  
 진행 개체에 대 한 GUID입니다.  
  
 `punk`  
 진행 디버거로 전달할 이벤트 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_NOTIMPL`|메서드가 현재 구현 되어 있지 않습니다.|  
  
## <a name="remarks"></a>주의  
 GUID 및 `IUnknown`의 의미 체계는 완전히 응용 프로그램/디버거 정의 됩니다.  
  
 이 메서드는 디버거 모델의 사용자 지정 확장을 허용 합니다. 현재는 구현 되어 있지 않습니다.  
  
 이 메서드를 호출 하면 `IApplicationDebugger::onDebuggerEvent` 호출 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Idebugapplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onDebuggerEvent](../../winscript/reference/iapplicationdebugger-ondebuggerevent.md)