---
title: 'IDebugFormatter:: GetVariantForString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugFormatter.GetVariantForString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugFormatter::GetVariantForString
ms.assetid: 2993431d-0ee2-4d8d-b62c-0a810a8bc391
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fc230caa861444b10b463e5786d5f8cb93ec32f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571523"
---
# <a name="idebugformattergetvariantforstring"></a>IDebugFormatter::GetVariantForString
지정 된 문자열을 포함 하는 VARIANT를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetVariantForString(  
   LPCOLESTR  pwstrValue,  
   VARIANT*   pvar  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pwstrValue`  
 진행 VARIANT에 저장할 문자열입니다.  
  
 `pvar`  
 제한이 @No__t_0를 포함 하는 VARIANT입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 지정 된 문자열을 포함 하는 VARIANT를 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugFormatter 인터페이스](../../winscript/reference/idebugformatter-interface.md)