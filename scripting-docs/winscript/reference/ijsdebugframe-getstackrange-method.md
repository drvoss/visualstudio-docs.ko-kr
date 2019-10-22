---
title: 'IJsDebugFrame:: GetStackRange 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetStackRange
apilocation:
- jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1ac3cbee9d16296632477f4128ec36370ab0d4a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574036"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange 메서드
논리적 JavaScript 스택 프레임의 절대 주소 범위를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pStart`  
 제한이 프레임의 가장 작은 스택 포인터입니다.  
  
 `pEnd`  
 제한이 프레임의 가장 상위 스태커 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 이 메서드는 여러 런타임에 수집 된 인터리브 스택 추적을 piecing 하는 데 유용 합니다. 시작, 종료 스택 포인터는 여러 물리적 컴퓨터 스택 프레임 (해석 된 JavaScript 런타임 프레임의 경우)을 포함할 수 있습니다. 스택이 높은 주소에서 낮은 주소로 증가 함에 따라 시작 > 종료 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugFrame 인터페이스](../../winscript/reference/ijsdebugframe-interface.md)