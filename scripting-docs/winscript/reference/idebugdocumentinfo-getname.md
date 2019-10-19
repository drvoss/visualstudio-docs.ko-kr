---
title: 'IDebugDocumentInfo:: GetName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetName
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetName
ms.assetid: c25d73da-99b6-4c9f-82af-182b4853f81c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bc098da29367a322bd93b4f60ba0e090aee9ee91
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570964"
---
# <a name="idebugdocumentinfogetname"></a>IDebugDocumentInfo::GetName
지정 된 문서 이름을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetName(  
   DOCUMENTNAMETYPE  dnt,  
   BSTR*             pbstrName  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dnt`  
 진행 반환할 문서 이름 형식입니다.  
  
 `pbstrName`  
 제한이 이름을 포함 하는 문자열입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_FAIL`|지정 된 문서 이름을 알 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 지정 된 문서 이름을 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [Idebugdocumentinfo 인터페이스](../../winscript/reference/idebugdocumentinfo-interface.md)    
 [DOCUMENTNAMETYPE 열거형](../../winscript/reference/documentnametype-enumeration.md)