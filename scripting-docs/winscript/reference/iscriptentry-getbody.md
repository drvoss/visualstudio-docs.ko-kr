---
title: 'IScriptEntry:: GetBody | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetBody
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetBody
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aba6019f4729f1b4a31933a4ca93c0eddf6159a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575480"
---
# <a name="iscriptentrygetbody"></a>IScriptEntry::GetBody
@No__t_0 스크립트 블록, 함수 블록 또는 scriptlet의 본문에 해당 하는 텍스트를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pbstr`  
 제한이 다음 중 하나의 본문에 있는 텍스트입니다.  
  
- @No__t_0 스크립트 블록  
  
- 함수 블록의 `IScriptEntry` 함수  
  
- @No__t_0 scriptlet 이벤트 처리기  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IScriptEntry 인터페이스](../../winscript/reference/iscriptentry-interface.md)