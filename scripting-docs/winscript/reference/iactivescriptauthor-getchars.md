---
title: 'IActiveScriptAuthor:: GetChars | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetChars
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetChars
ms.assetid: a73ba263-12f7-4d5f-b4c8-9ad7e2d5d3cb
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ce2b46d65c2ce92111bc4b6f44f66ce9dc4ce5f
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576246"
---
# <a name="iactivescriptauthorgetchars"></a>IActiveScriptAuthor::GetChars
요청 된 완료 컨텍스트의 완료 문자 집합을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetChars(  
   DWORD            fRequestedList,  
   BSTR             *pbstrChars  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `fRequestedList`  
 진행 요청 된 완료 컨텍스트입니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|0x0001|왼쪽 열거를 요청 합니다.|  
|SCRIPT_CMPL_MEMBER_TRIGGER|0x0002|멤버 완료 컨텍스트를 요청 합니다.|  
|SCRIPT_CMPL_PARAM_TRIGGER|0x0003|매개 변수 목록을 요청 합니다.|  
|SCRIPT_CMPL_COMMIT|0x0004|매개 변수 목록의 완료를 요청 합니다.|  
  
 `pbstrChars`  
 제한이 요청 된 완료 컨텍스트에 해당 하는 문자입니다.  
  
|`fRequestedList` 매개 변수|반환 된 문자|  
|--------------------------------|-------------------------|  
|SCRIPT_CMPL_ENUM_TRIGGER|"."|  
|SCRIPT_CMPL_MEMBER_TRIGGER|"="|  
|SCRIPT_CMPL_PARAM_TRIGGER|"(,"|  
|SCRIPT_CMPL_COMMIT|"()"|  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)