---
title: 'IApplicationDebugger:: onDebuggerEvent | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onDebuggerEvent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onDebuggerEvent
ms.assetid: 82a5faaa-1222-4bf1-8569-10439dbdf16d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8edb2a3c39d639b5b6722707d7b6c0b57a5c19
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577859"
---
# <a name="iapplicationdebuggerondebuggerevent"></a>IApplicationDebugger::onDebuggerEvent
사용자 지정 응용 프로그램 이벤트를 처리 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT onDebuggerEvent(  
   REFIID     riid,  
   IUnknown*  punk  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `riid`  
 진행 개체에 대 한 인터페이스 식별자입니다.  
  
 `punk`  
 진행 `riid`에서 정의 된 인터페이스를 구현 하는 이벤트 개체입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_NOTIMPL`|메서드가 현재 구현 되어 있지 않습니다.|  
  
## <a name="remarks"></a>주의  
 `IUnknown`의 의미 체계는 완전히 응용 프로그램/디버거 정의 됩니다.  
  
 이 메서드는 디버거 모델의 사용자 지정 확장을 허용 합니다. 현재는 구현 되어 있지 않습니다.  
  
 이 메서드는 `IDebugApplication::FireDebuggerEvent`가 호출 될 때 호출 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Iapplicationdebugger 인터페이스](../../winscript/reference/iapplicationdebugger-interface.md)   
 [IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)