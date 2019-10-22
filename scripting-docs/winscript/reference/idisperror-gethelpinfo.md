---
title: 'IDispError:: GetHelpInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispError.GetHelpInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDispError::GetHelpInfo
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a84e57e97bb781ad3ea0be1ac6766fd94f6f5c30
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573125"
---
# <a name="idisperrorgethelpinfo"></a>IDispError::GetHelpInfo
가능한 경우 도움말 파일의 경로와 오류를 설명 하는 항목의 컨텍스트 ID를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrFileName`  
 제한이 도움말 파일의 정규화 된 경로를 포함 하는 문자열입니다. 도움말 파일이 없거나 오류가 발생 한 경우 반환 값은 NULL입니다.  
  
 `pdwContext`  
 제한이 오류에 대 한 도움말 컨텍스트 ID입니다. 도움말 파일이 없는 경우 (`pbstrFileName`가 NULL 인 경우)이 매개 변수는 의미가 없습니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_FAIL`|공급자별 오류가 발생 했습니다.|  
|`E_INVALIDARG`|`pbstrFileName` 또는 `pdwContext`가 NULL입니다.|  
|`E_OUTOFMEMORY`|공급자가 도움말 파일 경로를 반환할 충분 한 메모리를 할당할 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 가능한 경우 오류를 설명 하는 토픽의 컨텍스트 ID와 도움말 파일의 경로를 반환 합니다.  
  
> [!NOTE]
> 이 메서드는 구현 되지 않습니다.  
  
## <a name="see-also"></a>참조  
 [IDispError 인터페이스](../../winscript/reference/idisperror-interface.md)