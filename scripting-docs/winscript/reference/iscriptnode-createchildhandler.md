---
title: 'IScriptNode:: CreateChildHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e024bb7d6a81b35994edddfe9e71666b0ee8df0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573597"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Scriptlet를 `IScriptNode`의 자식 인스턴스로 추가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszDefaultName`  
 진행 Scriptlet와 연결할 기본 이름의 주소입니다.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] 호스트의 정규화 된 이름에서 가져온 식별자 목록입니다.  
  
 `cpszNames`  
 진행 `prgpszNames` 매개 변수의 식별자 수입니다.  
  
 `pszEvent`  
 진행 Scriptlet 연결 된 이벤트 이름을 식별 하는 버퍼 주소입니다.  
  
 `pszDelimiter`  
 진행 스크립트 블록 끝 구분 기호의 주소입니다. 구문 분석을 위해 호스트는 일반적으로 두 개의 작은따옴표와 같은 구분 기호를 사용 하 여 스크립트 블록의 끝을 검색 합니다.  
  
 구분 기호는 스크립트 작성 엔진에서 전처리를 사용 하도록 설정 합니다. 예를 들어, 엔진은 구분 기호로 사용할 작은따옴표를 두 개의 작은따옴표로 바꿀 수 있습니다. 엔진은 구분 기호가 사용 되는 방법을 결정 합니다.  
  
 스크립트 블록의 끝을 식별 하는 구분 기호를 사용 하지 않는 경우 NULL로 설정 합니다.  
  
 `ptiSignature`  
 진행 함수 개체에 대 한 형식 정보입니다.  
  
 `iMethodSignature`  
 진행 `ITypeInfo``ptiSignature` 매개 변수에 있는 함수의 인덱스입니다.  
  
 `isn`  
 진행 부모에 있는 자식의 인덱스입니다.  
  
 `dwCookie`  
 진행 항목을 호스트 개체와 연결 하는 데 사용 되는 응용 프로그램 정의 값입니다.  
  
 `ppse`  
 제한이 자식 인스턴스의 `IScriptEntry` 인터페이스에 대 한 포인터를 받는 변수의 주소입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 Scriptlet는 이벤트 처리기를 지정 합니다. 이 메서드는 웹 페이지를 나타내는 `IScriptNode` 개체에 의해 호출 되는 경우 scriptlet를 만듭니다. 다른 인터페이스에서 호출 하는 경우에는이 메서드가 성공 하지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Iscriptnode 인터페이스](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 인터페이스](../../winscript/reference/iscriptentry-interface.md)