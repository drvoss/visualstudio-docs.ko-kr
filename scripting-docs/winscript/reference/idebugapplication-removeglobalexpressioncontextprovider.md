---
title: 'IDebugApplication:: RemoveGlobalExpressionContextProvider | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.RemoveGlobalExpressionContextProvider
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::RemoveGlobalExpressionContextProvider
ms.assetid: ace638a3-ed34-4d20-8404-45c684aaaf1a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b4b948cea02d696b6c176e925adf9c95913be2cd
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571145"
---
# <a name="idebugapplicationremoveglobalexpressioncontextprovider"></a>IDebugApplication::RemoveGlobalExpressionContextProvider
이 응용 프로그램에서 전역 식 컨텍스트 공급자를 제거 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT RemoveGlobalExpressionContextProvider(  
   DWORD_PTR  dwCookie  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwCookie`  
 진행 전역 컨텍스트 공급자를 추가할 때 `AddGlobalExpressionContextProvider` 메서드에서 반환 되는 쿠키입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 @No__t_0 메서드는이 응용 프로그램에서 전역 식 컨텍스트 공급자를 제거 합니다.  
  
## <a name="see-also"></a>참조  
 [Idebugapplication:: AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)    
 [IDebugApplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)