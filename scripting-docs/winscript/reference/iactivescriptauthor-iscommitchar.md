---
title: 'IActiveScriptAuthor:: IsCommitChar | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.IsCommitChar
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::IsCommitChar
ms.assetid: 7857c6f9-61e6-41e5-8e01-f56588c10421
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2f442bdc22f569cac6d706d739b2cfb37e07398b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576347"
---
# <a name="iactivescriptauthoriscommitchar"></a>IActiveScriptAuthor::IsCommitChar
지정 된 문자가 응용 프로그램에 의해 문 완성 커밋을 트리거해야 하는지 여부를 나타내는 값을 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT IsCommitChar(  
   OLECHAR    ch,  
   BOOL       *pfcommit  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ch`  
 진행 테스트할 문자입니다.  
  
 `pfcommit`  
 [out] 문자가 커밋 문자인 경우 `True` 합니다. 그렇지 않으면 `False` 합니다.  
  
## <a name="return-value"></a>반환 값  
 `HRESULT`입니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
  
## <a name="see-also"></a>참조  
 [IActiveScriptAuthor 인터페이스](../../winscript/reference/iactivescriptauthor-interface.md)