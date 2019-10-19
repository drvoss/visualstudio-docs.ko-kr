---
title: 'IDebugDocumentHost:: GetPathName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetPathName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetPathName
ms.assetid: 8abe2a86-e467-4ac9-8ccb-8761141bfa0d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33ebcde4cf1db28e199f13fae720374bd1b64763
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569286"
---
# <a name="idebugdocumenthostgetpathname"></a>IDebugDocumentHost::GetPathName
문서 소스 파일의 전체 경로 및 파일 이름을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetPathName(  
   BSTR*  pbstrLongName,  
   BOOL*  pfIsOriginalFile  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstrLongName`  
 제한이 긴 이름을 포함 하는 문자열입니다.  
  
 `pfIsOriginalFile`  
 제한이 @No__t_0에서 문서의 원본 파일을 참조 하면 true이 고, 그렇지 않으면 false 인 플래그입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_FAIL`|원본 파일을 만들거나 확인할 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 문서 소스 파일의 전체 경로 및 파일 이름을 반환 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentHost 인터페이스](../../winscript/reference/idebugdocumenthost-interface.md)