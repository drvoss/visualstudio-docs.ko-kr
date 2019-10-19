---
title: 'IDispError:: QueryErrorInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.QueryErrorInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::QueryErrorInfo
ms.assetid: e7e71a14-77e2-4331-9ffc-1dace041fa84
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ccfcb020faf25fbe1723a384ff08aefcf55b56d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573083"
---
# <a name="idisperrorqueryerrorinfo"></a>IDispError::QueryErrorInfo
특정 유형의 오류 정보를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT QueryErrorInfo(  
   GUID  guidErrorType,  
   IDispError**  ppde  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `guidErrorType`  
 진행 오류 유형을 지정 하는 GUID입니다.  
  
 `ppde`  
 제한이 IDispError 개체를 지정 합니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 @No__t_0 메서드는 특정 유형의 오류 정보를 검색 합니다.  
  
> [!NOTE]
> 이 메서드는 구현 되지 않습니다.  
  
## <a name="see-also"></a>참조  
 [IDispError 인터페이스](../../winscript/reference/idisperror-interface.md)