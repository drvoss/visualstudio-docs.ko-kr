---
title: 'IScriptNode:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c58ff83c43a1418e6fb7bd8945afa181af60c68a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573610"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
`IScriptEntry`의 자식 인스턴스를 추가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `isn`  
 진행 부모에 있는 자식의 인덱스입니다.  
  
 `dwCookie`  
 진행 자식 항목을 호스트 개체와 연결 하는 데 사용 되는 응용 프로그램 정의 값입니다.  
  
 `pszDelimiter`  
 진행 스크립트 블록 끝 구분 기호의 주소입니다. 구문 분석을 위해 호스트는 일반적으로 두 개의 작은따옴표와 같은 구분 기호를 사용 하 여 스크립트 블록의 끝을 검색 합니다.  
  
 구분 기호를 사용 하 여 스크립트 제작 엔진이 전처리를 제공할 수 있습니다. 예를 들어, 엔진은 구분 기호로 사용할 작은따옴표를 두 개의 작은따옴표로 바꿀 수 있습니다. 엔진은 구분 기호가 사용 되는 방법을 결정 합니다.  
  
 구분 기호가 스크립트 블록의 끝을 표시 하지 않는 경우 NULL로 설정 합니다.  
  
 `ppse`  
 제한이 자식 인스턴스의 `IScriptEntry` 인터페이스에 대 한 포인터를 받는 변수의 주소입니다.  
  
 웹 페이지를 나타내는 `IScriptNode` 개체의 경우이 매개 변수는 스크립트 블록을 지정 하는 `IScriptEntry` 인스턴스를 반환 합니다.  
  
 스크립트 블록을 나타내는 `IScriptEntry` 개체의 경우이 매개 변수는 함수 개체를 지정 하는 `IScriptEntry` 인스턴스를 반환 합니다.  
  
 함수 개체를 나타내는 `IScriptEntry` 개체의 경우이 메서드는 실패 합니다.  
  
 `IScriptScriptlet` 개체의 경우이 메서드는 실패 합니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 `IScriptNode` 인터페이스는 웹 페이지 또는 해당 요소를 나타냅니다. `IScriptNode`에서 파생 된 `IScriptEntry` 인터페이스는 스크립트 블록이 나 함수 개체를 나타냅니다. `IScriptEntry`에서 파생 된 `IScriptScriptlet` 인터페이스는 이벤트 처리기를 나타냅니다.  
  
## <a name="see-also"></a>참고 항목  
 [Iscriptnode 인터페이스](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 인터페이스](../../winscript/reference/iscriptentry-interface.md)