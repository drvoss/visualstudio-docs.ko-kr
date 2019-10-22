---
title: 'IActiveScriptAuthor:: AddScriptlet | Microsoft Docs'
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
ms.openlocfilehash: 3a349a848f282e6b3a228c7b17009e0261801be5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577981"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Scriptlet 코드를 루트 수준 `IScriptNode` 개체의 자식으로 추가 합니다. 호스트에서 scriptlet의 정규화 된 이름에는 두 수준만 사용할 수 있습니다.  
  
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
 진행 Scriptlet와 연결할 기본 이름의 주소입니다.  
  
 `pszCode`  
 진행 Scriptlet 텍스트의 주소입니다.  
  
 `pszItemName`  
 진행 호스트에서 정규화 된 scriptlet name의 최상위 식별자에 대 한 버퍼 주소입니다.  
  
 `pszSubItemName`  
 진행 호스트에서 정규화 된 scriptlet 이름의 두 번째 수준 식별자에 대 한 버퍼 주소입니다. 이름에 수준이 하나뿐인 경우 NULL로 설정 합니다.  
  
 `pszEventName`  
 진행 Scriptlet가 이벤트 처리기 인 이벤트 이름을 포함 하는 버퍼의 주소입니다.  
  
 `pszDelimiter`  
 진행 스크립트 블록 끝 구분 기호의 주소입니다. 텍스트 스트림에서 `pszCode` 구문 분석 되는 경우 호스트는 일반적으로 구분 기호 (예: 두 개의 작은따옴표)를 사용 하 여 스크립트 블록의 끝을 검색 합니다. 구분 기호가 스크립트 블록의 끝을 표시 하지 않는 경우이 매개 변수를 NULL로 설정 합니다.  
  
 `dwCookie`  
 진행 Scriptlet을 호스트 개체와 연결 하는 데 사용 되는 응용 프로그램 정의 값입니다.  
  
 `dwFlags`  
 진행 사용 되지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)