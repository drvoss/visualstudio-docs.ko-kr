---
title: 'IActiveScriptAuthor:: GetLanguageFlags | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68da16513050bd87642be2c96212a330a0916608
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576197"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
언어 정보를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pgrfasa`  
 제한이 언어 정보를 포함 하는 플래그입니다. 은 다음 값을 조합 하 여 사용할 수 있습니다.  
  
|상수|값|설명|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|언어는 응용 프로그램 대신 스크립트 작성 엔진에서 스크립트 이벤트 처리기를 만들도록 선호 합니다.|  
|fasaSupportInternalHandler|0x0002|이 언어는 스크립트 작성 엔진에서 만든 스크립트 이벤트 처리기를 지원 합니다.|  
|fasaCaseSensitive|0x0004|스크립트 언어는 대/소문자를 구분 합니다.|  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 스크립트 작성 엔진이 이벤트 처리기를 관리 하는 경우 응용 프로그램은 `IScriptEntry` 개체에서 `CreateChildHandler`를 호출 해야 합니다. 그러면 이벤트 처리기에 해당 하는 `IScriptScriptlet` 개체가 만들어집니다. 또한 엔진은 스크립트 항목에 이벤트 처리기를 추가 합니다. 이벤트 처리기는 지정 된 서명 정보를 포함 하는 빈 함수입니다.  
  
 응용 프로그램에서 이벤트 처리기를 관리 하는 경우 scriptlet 이벤트 처리기를 나타내는 `IScriptNode` 개체에서 `CreateChildHandler`를 호출 해야 합니다. 그러면 이벤트 처리기 scriptlet 연결 된 `IScriptScriptlet` 개체가 만들어집니다. 또한 응용 프로그램에서는 새 `IScriptEntry` 개체 또는 기존 개체에 빈 함수를 이벤트 처리기로 추가 해야 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)