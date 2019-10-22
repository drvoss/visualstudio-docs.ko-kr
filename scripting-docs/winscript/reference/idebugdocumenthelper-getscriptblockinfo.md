---
title: 'IDebugDocumentHelper:: GetScriptBlockInfo | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.GetScriptBlockInfo
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::GetScriptBlockInfo
ms.assetid: 332d7540-bbbe-4747-95ec-e47384d4f4e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a92aa00d7997ceccc583c88a070f6fbc7d4359d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576093"
---
# <a name="idebugdocumenthelpergetscriptblockinfo"></a>IDebugDocumentHelper::GetScriptBlockInfo
스크립트 블록에 해당 하는 문자 및 스크립트 엔진의 범위를 검색 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetScriptBlockInfo(  
   DWORD_PTR        dwSourceContext,  
   IActiveScript**  ppasd,  
   ULONG*           piCharPos,  
   ULONG*           pcChars  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dwSourceContext`  
 진행 스크립트 블록의 소스 컨텍스트입니다.  
  
 `ppasd`  
 제한이 이 스크립트 블록에 대 한 스크립트 엔진입니다.  
  
 `piCharPos`  
 제한이 스크립트 블록의 시작 위치입니다.  
  
 `cChars`  
 제한이 스크립트 블록의 문자 수입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드는 스크립트 블록에 해당 하는 문자 및 스크립트 엔진의 범위를 검색 합니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentHelper 인터페이스](../../winscript/reference/idebugdocumenthelper-interface.md)