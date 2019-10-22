---
title: 'IActiveScriptAuthor:: AddTypeLib | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddTypeLib
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bd96732a905d3fc0732ccfeaf2b65ada82957f4
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577222"
---
# <a name="iactivescriptauthoraddtypelib"></a>IActiveScriptAuthor::AddTypeLib
스크립트에 대 한 네임 스페이스에 형식 라이브러리를 추가 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `rguidTypeLib`  
 진행 추가할 형식 라이브러리의 CLSID (클래스 식별자)입니다.  
  
 `dwMajor`  
 진행 주 버전 번호입니다.  
  
 `dwMinor`  
 진행 부 버전 번호입니다.  
  
 `dwFlags`  
 진행 사용 되지 않습니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 `LoadTypeLib`를 호출 하 여 형식 라이브러리를 로드 합니다. 성공 하면이 메서드는 `IActiveScriptAuthor::AddNamedItem`를 호출 하 여 형식 정보를 추가 합니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)    
 [IActiveScriptAuthor:: AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)    
 [LoadTypeLib](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelib)