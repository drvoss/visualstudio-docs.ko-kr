---
title: 'IDebugExpressionContext:: GetLanguageInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpressionContext.GetLanguageInfo
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpressionContext::GetLanguageInfo
ms.assetid: 35e25662-0b2a-4c3f-bce4-f01726bc04a8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e6dd3d3bb254cd91f411da3b6b587bc37c3a777
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576403"
---
# <a name="idebugexpressioncontextgetlanguageinfo"></a>IDebugExpressionContext::GetLanguageInfo
이 컨텍스트를 소유 하는 언어의 이름 및 GUID를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetLanguageInfo(  
   BSTR*  pbstrLanguageName,  
   GUID*  pLanguageID  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrLanguageName`  
 제한이 언어의 이름입니다.  
  
 `pLanguageID`  
 제한이 언어에 대 한 고유 id입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는이 컨텍스트를 소유 하는 언어에 대 한 이름 및 GUID를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugExpressionContext 인터페이스](../../winscript/reference/idebugexpressioncontext-interface.md)