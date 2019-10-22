---
title: 'IDebugApplicationNode100:: QueryIsChildNode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::QueryIsChildNode
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 761b2800415adbcf298eb96f2231a74195b2291c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574739"
---
# <a name="idebugapplicationnode100queryischildnode"></a>IDebugApplicationNode100::QueryIsChildNode
지정 된 문서가이 노드의 자식 노드 중 하나에 속하는지 여부를 확인 합니다.  
  
> [!IMPORTANT]
> [IDebugApplicationNode100 인터페이스](../../winscript/reference/idebugapplicationnode100-interface.md) 는 PDM v 10.0 이상에서 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT QueryIsChildNode(        [in] IDebugDocument* pSearchKey        );  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pSearchKey`  
 검색 키입니다.  
  
## <a name="see-also"></a>참조  
 [IDebugApplicationNode100 인터페이스](../../winscript/reference/idebugapplicationnode100-interface.md)