---
title: 'Ijsdebugframe:: Evaluate 메서드 | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b328d6071ae9dc96b8e7f62bad6d4417aa1730f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62558192"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate 메서드
이 스택 프레임의 컨텍스트에서 식을 계산 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pExpressionText`  
 [in] 계산할 식입니다.  
  
 `ppDebugProperty`  
 [out] 속성 브라우저를 나타내는 개체입니다.  
  
 `pError`  
 [out] 오류가 발생 하는 경우 오류 메시지입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>설명  
 다음을 반환합니다. S_OK: 평가 성공, * ppDebugProperty는 평가 결과 포함 합니다. S_FALSE: 평가 오류를 throw 합니다 (또는 평가 작업이 지원 되지 않습니다), \*pError는 오류 메시지를 포함 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참고 항목  
 [IJsDebugFrame 인터페이스](../../winscript/reference/ijsdebugframe-interface.md)