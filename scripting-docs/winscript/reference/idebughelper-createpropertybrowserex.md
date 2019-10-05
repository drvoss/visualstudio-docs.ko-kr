---
title: IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01e63d1588fd1e25f3415f22450ed5145752d711
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979203"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
VARIANT를 래핑하고 VARIANT 값 또는 VARTYPE 형식 문자열을 사용자 지정 변환에 대 한 허용 하는 속성 브라우저를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pvar`  
 [in] 이동할 루트 variant입니다.  
  
 `bstrName`  
 [in] 루트를 지정할 이름입니다.  
  
 `pdat`  
 [in] 속성을 요청 하는 스레드입니다. 이 매개 변수가 NULL 이면 없습니다 마샬링을 수행 됩니다.  
  
 `pdf`  
 [in] 변형에 대 한 사용자 지정 서식 지정을 제공 하는 개체입니다.  
  
 `ppdob`  
 [out] 속성 브라우저입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 이 메서드는 VARIANT를 래핑하고 VARIANT 값 또는 VARTYPE 형식 문자열을 사용자 지정 변환에 대 한 허용 하는 속성 브라우저를 반환 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper 인터페이스](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)