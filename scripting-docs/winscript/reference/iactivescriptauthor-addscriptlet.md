---
title: IActiveScriptAuthor::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64df7bd4c0d0dde303cdc15d7111688d14c7dc49
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935460"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
루트 수준 자식으로 추가 하는 코드 스크립트릿 `IScriptNode` 개체입니다. 호스트에서 scriptlet의 정규화 된 이름에 두 수준이 허용 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszDefaultName`  
 [in] Scriptlet과 연결 된 기본 이름의 주소입니다.  
  
 `pszCode`  
 [in] Scriptlet 텍스트의 주소입니다.  
  
 `pszItemName`  
 [in] 버퍼의 주소는 호스트에서 이름 정규화 scriptlet의 최상위 식별자입니다.  
  
 `pszSubItemName`  
 [in] 버퍼의 주소는 호스트의 정규화 된 scriptlet 이름의 두 번째 수준 식별자입니다. 이름에 하나의 수준만 NULL로 설정 합니다.  
  
 `pszEventName`  
 [in] Scriptlet을 이벤트 처리기가 이벤트 이름을 포함 하는 버퍼의 주소입니다.  
  
 `pszDelimiter`  
 [in] 주소 끝의 스크립트 블록 구분 기호입니다. 때 `pszCode` 구문 분석은 텍스트의 스트림에서 호스트 일반적으로 구분 기호가 사용 (예: 두 개의 작은따옴표), 스크립트 블록의 끝을 검색 합니다. 구분 기호를 스크립트 블록의 끝을 표시 하지 않는 경우이 매개 변수를 NULL로 설정 합니다.  
  
 `dwCookie`  
 [in] 호스트 개체를 사용 하 여 scriptlet을 연결 하는 데 사용 되는 응용 프로그램 정의 값입니다.  
  
 `dwFlags`  
 [in] 사용 되지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
  
## <a name="see-also"></a>참고 항목  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)