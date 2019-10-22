---
title: 'IActiveScriptSite:: GetDocVersionString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ecc592b6b7fcae5f516a3c1dd111c027e67b6dc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571125"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
현재 문서 버전을 고유 하 게 식별 하는 호스트 정의 문자열을 검색 합니다. 메모장을 사용 하 여 HTML 페이지를 편집 하는 경우와 같이 관련 문서가 Windows 스크립트의 범위 외부에서 변경 된 경우 스크립팅 엔진은 다음에 스크립트가 로드 될 때 다시 컴파일을 강제로 수행 하 여 지속형 상태와 함께이를 저장할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pstrVersionString`  
 제한이 호스트 정의 문서 버전 문자열의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 `S_OK`을 반환 하 고,이 메서드가 지원 되지 않는 경우 `E_NOTIMPL`을 반환 합니다.  
  
## <a name="remarks"></a>주의  
 @No__t_0 반환 되는 경우 스크립팅 엔진은 스크립트가 문서와 동기화 되어 있다고 가정 해야 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)