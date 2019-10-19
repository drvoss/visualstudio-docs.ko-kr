---
title: 'IJsDebugFrame:: Evaluate 메서드 | Microsoft Docs'
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
ms.openlocfilehash: 6227b97c1fd5fae32db3e13ef72751726c36b043
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573492"
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
 진행 계산할 식입니다.  
  
 `ppDebugProperty`  
 제한이 속성 브라우저를 나타내는 개체입니다.  
  
 `pError`  
 제한이 오류가 발생 한 경우의 오류 메시지입니다.  
  
## <a name="return-value"></a>반환 값  
  
## <a name="remarks"></a>주의  
 다음을 반환 합니다. S_OK: Evaluation 성공, * ppDebugProperty에 평가 결과가 포함 됩니다. S_FALSE: 오류 메시지를 포함 하는 \*pError (또는 계산 작업이 지원 되지 않음)가 발생 합니다.  
  
## <a name="requirements"></a>요구 사항  
 **헤더:** jscript9diag.h  
  
## <a name="see-also"></a>참조  
 [IJsDebugFrame 인터페이스](../../winscript/reference/ijsdebugframe-interface.md)