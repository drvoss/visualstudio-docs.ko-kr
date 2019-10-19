---
title: 'IDebugHelper:: CreatePropertyBrowser | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 99aa03470b49d02ee9f0ac1548bd1f8e27d0ab34
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72562491"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
VARIANT를 래핑하는 속성 브라우저를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pvar`  
 진행 찾아볼 루트 variant입니다.  
  
 `bstrName`  
 진행 루트에 지정할 이름입니다.  
  
 `pdat`  
 진행 속성을 요청 하는 스레드입니다. 이 매개 변수가 NULL 이면 마샬링이 수행 되지 않습니다.  
  
 `ppdob`  
 제한이 속성 브라우저입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 VARIANT를 래핑하는 속성 브라우저를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugHelper:: CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)    
 [IDebugHelper 인터페이스](../../winscript/reference/idebughelper-interface.md)    
 [IDebugProperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)