---
title: 'IApplicationDebuggerUI:: BringDocumentContextToTop | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebuggerUI.BringDocumentContextToTop
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebuggerUI::BringDocumentContextToTop
ms.assetid: 7844217d-658b-42af-8d10-2714f4eded20
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8648a4377e901908df20cdb5f413ee73ede5c1a6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577806"
---
# <a name="iapplicationdebuggeruibringdocumentcontexttotop"></a>IApplicationDebuggerUI::BringDocumentContextToTop
지정 된 문서 컨텍스트를 포함 하는 창을 디버거 사용자 인터페이스의 맨 위에 표시 하 고 창을 컨텍스트로 스크롤합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT BringDocumentContextToTop(  
   IDebugDocumentContext*  pddc  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pddc`  
 진행 디버거 사용자 인터페이스에서 위쪽으로 가져오기 위한 문서 컨텍스트입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드는 `HRESULT`를 반환 합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
|`E_INVALIDARG`|@No__t_0에서 지정한 컨텍스트를 알 수 없습니다.|  
  
## <a name="remarks"></a>주의  
 이 메서드는 지정 된 문서 컨텍스트를 포함 하는 창을 디버거 사용자 인터페이스의 맨 위에 표시 하 고 창을 컨텍스트로 스크롤합니다.  
  
## <a name="see-also"></a>참조  
 [IApplicationDebuggerUI 인터페이스](../../winscript/reference/iapplicationdebuggerui-interface.md)