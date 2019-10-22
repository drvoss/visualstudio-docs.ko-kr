---
title: 'IDebugApplication:: StepOutComplete | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.StepOutComplete
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::StepOutComplete
ms.assetid: 9675b214-7be5-4cf7-a63f-7865f3c54371
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f50d7e8a8936e52f4177450e7d163c4cfeaa55df
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571042"
---
# <a name="idebugapplicationstepoutcomplete"></a>IDebugApplication::StepOutComplete
단일 단계 모드의 언어 엔진이 호출자에 게 반환 될 것을 프로세스 디버그 관리자에 게 알립니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT StepOutComplete();  
```  
  
#### <a name="parameters"></a>매개 변수  
 이 메서드는 매개 변수를 사용 하지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 언어 엔진은 호출자에 게 반환 되기 바로 전에 단일 단계 모드에서이 메서드를 호출 합니다. 프로세스 디버그 관리자는이 기회를 사용 하 여 첫 번째 기회에서 중단 되어야 하는 다른 모든 스크립트 엔진에 알립니다. 이 기법은 언어 간 단계 모드를 구현 하는 방법입니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)