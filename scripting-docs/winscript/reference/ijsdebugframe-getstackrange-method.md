---
title: 'Ijsdebugframe:: Getstackrange 메서드 | Microsoft Docs'
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
ms.openlocfilehash: 52dd6114d3ec462f91f8bce5e76f73c5487746ed
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558218"
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange 메서드
논리 JavaScript 스택 프레임의 절대 주소 범위를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pStart`  
 [out] 최하위 프레임의 스택 포인터입니다.  
  
 `pEnd`  
 [out] 상위 프레임의 최상위 스택 포인터입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>설명  
 이 메서드는 여러 런타임에서 수집 된 인터리브된 스택 추적 하나로 결합 하는 데 유용 합니다. 시작, 끝 스택 포인터에는 여러 물리적 컴퓨터 스택 프레임 (해석 된 JavaScript 런타임 프레임) 포함 될 수 있습니다. 시작 > 스택이 높은에서 낮은 주소로 증가 하는 대로 종료 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [IJsDebugFrame 인터페이스](../../winscript/reference/ijsdebugframe-interface.md)