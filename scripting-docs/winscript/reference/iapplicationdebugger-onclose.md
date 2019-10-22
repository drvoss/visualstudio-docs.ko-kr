---
title: 'IApplicationDebugger:: onClose | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.onClose
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::onClose
ms.assetid: f3d6ca9f-6697-4d02-9d1a-16e3859bf282
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e31b2a77effc729f0e7df1e36116ee554446093
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577882"
---
# <a name="iapplicationdebuggeronclose"></a>IApplicationDebugger::onClose
디버그 응용 프로그램 닫기 이벤트를 처리 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT onClose();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 `IDebugApplication::Close`가 호출 될 때 호출 됩니다.  
  
## <a name="see-also"></a>참조  
 [Iapplicationdebugger 인터페이스](../../winscript/reference/iapplicationdebugger-interface.md)    
 [IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)