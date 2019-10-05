---
title: IScriptNode::CreateChildHandler | Microsoft Docs
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
ms.openlocfilehash: bca8b30021d39638f3755bace2625bb38a44242d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787146"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
자식 인스턴스는 scriptlet 추가 `IScriptNode`합니다.  
  
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
 [in] Scriptlet과 연결 된 기본 이름의 주소입니다.  
  
 `prgpszNames`  
 [에 size_is (`cpszNames`)]에서 호스트의 정규화 된 이름 식별자 목록입니다.  
  
 `cpszNames`  
 [in] 식별자의 수를 `prgpszNames` 매개 변수입니다.  
  
 `pszEvent`  
 [in] Scriptlet과 연결 된 이벤트 이름을 식별 하는 버퍼 주소입니다.  
  
 `pszDelimiter`  
 [in] 주소 끝의 스크립트 블록 구분 기호입니다. 구문 분석에 대 한 호스트 일반적으로 사용 하 여 구분 기호 (예: 두 개의 작은따옴표), 스크립트 블록의 끝을 찾습니다.  
  
 구분 기호는 전처리 스크립트 엔진을 작성 하 여 수 있습니다. 예를 들어, 엔진은 두 개의 작은따옴표를 구분 기호로 사용 하기 위해 사용 하 여 작은따옴표를 바꿀 수 있습니다. 엔진은 구분 기호를 사용 하는 방법을 결정 합니다.  
  
 구분 기호가 없습니다 스크립트 블록의 끝을 식별 하는 경우 NULL로 설정 합니다.  
  
 `ptiSignature`  
 [in] 함수 개체에 대 한 형식 정보입니다.  
  
 `iMethodSignature`  
 [in] 인덱스의 함수는 `ITypeInfo``ptiSignature` 매개 변수입니다.  
  
 `isn`  
 [in] 부모에서 자식 항목의 인덱스입니다.  
  
 `dwCookie`  
 [in] 호스트 개체를 사용 하 여 항목을 연결 하는 데 사용 되는 응용 프로그램 정의 값입니다.  
  
 `ppse`  
 [out] 에 대 한 포인터를 받는 변수의 주소는 `IScriptEntry` 자식 인스턴스는 인터페이스입니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 Scriptlet을 이벤트 처리기를 지정 합니다. 에 의해 호출 되는 경우이 메서드는 scriptlet을 만듭니다는 `IScriptNode` 웹 페이지를 나타내는 개체입니다. 이 메서드는 다른 인터페이스에서 호출 되 면 성공 하지 않습니다.  
  
## <a name="see-also"></a>참고 항목  
 [IScriptNode 인터페이스](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry 인터페이스](../../winscript/reference/iscriptentry-interface.md)