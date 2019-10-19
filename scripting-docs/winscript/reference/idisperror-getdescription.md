---
title: 'IDispError:: GetDescription | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetDescription
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetDescription
ms.assetid: 04deaea6-0265-4e34-952e-634edba0e923
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d1bb1c3516c2601707e1a0bcd69f4f8409514fe
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573149"
---
# <a name="idisperrorgetdescription"></a>IDispError::GetDescription
오류에 대 한 텍스트 설명을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDescription(  
   BSTR*  pbstrDescription  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrDescription`  
 제한이 오류에 대 한 간단한 설명을 포함 하는 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 오류가 발생 한 메서드에 대 한 `IDispatchEx::InvokeEx`에 전달 된 LCID (로캘 id)로 지정 된 언어로 텍스트가 반환 됩니다.  
  
> [!NOTE]
> 이 메서드는 구현 되지 않습니다.  
  
## <a name="see-also"></a>참조  
 [IDispError 인터페이스](../../winscript/reference/idisperror-interface.md)    
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)