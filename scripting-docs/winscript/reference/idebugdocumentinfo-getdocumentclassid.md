---
title: 'IDebugDocumentInfo:: GetDocumentClassId | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentInfo.GetDocumentClassId
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentInfo::GetDocumentClassId
ms.assetid: 3b858794-2c0c-42ba-b98c-cd820ebace20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 996e6d751807bba1e1a74cbb7e579db25193c32b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569076"
---
# <a name="idebugdocumentinfogetdocumentclassid"></a>IDebugDocumentInfo::GetDocumentClassId
문서 유형을 식별 하는 `CLSID`를 반환 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT GetDocumentClassId(  
   CLSID*  pclsidDocument  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pclsidDocument`  
 제한이 문서 유형을 식별 하는 `CLSID`입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 이 메서드를 사용 하면 디버거 IDE에서이 문서에 대 한 사용자 지정 뷰어를 호스트할 수 있습니다.  
  
 문서에 볼 수 있는 데이터가 없으면 `pclsidDocument`의 반환 값이 `CLSID_NULL` 됩니다.  
  
## <a name="see-also"></a>참조  
 [IDebugDocumentInfo 인터페이스](../../winscript/reference/idebugdocumentinfo-interface.md)