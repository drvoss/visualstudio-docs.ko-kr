---
title: 'IDebugApplicationNode100:: GetExcludedDocuments | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::GetExcludedDocuments
ms.assetid: d44583a7-0b0b-4799-b075-837ad1da1946
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c135aa85ca65a44f6f970e83d7975bb441ff56f5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574750"
---
# <a name="idebugapplicationnode100getexcludeddocuments"></a>IDebugApplicationNode100::GetExcludedDocuments
지정 된 필터에 의해 숨겨진 텍스트 문서를 가져옵니다.  
  
> [!IMPORTANT]
> [IDebugApplicationNode100 인터페이스](../../winscript/reference/idebugapplicationnode100-interface.md) 는 PDM v 10.0 이상에서 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetExcludedDocuments(        [in] APPLICATION_NODE_EVENT_FILTER filter,        [out] TEXT_DOCUMENT_ARRAY* pDocuments        );  
```  
  
#### <a name="parameters"></a>매개 변수  
 `filter`  
 필터입니다.  
  
 `pDocuments`  
 문서 집합입니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplicationNode100 인터페이스](../../winscript/reference/idebugapplicationnode100-interface.md)