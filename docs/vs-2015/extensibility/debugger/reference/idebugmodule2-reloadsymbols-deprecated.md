---
title: IDebugModule2::ReloadSymbols_Deprecated | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugModule2::ReloadSymbols
helpviewer_keywords:
- IDebugModule2::ReloadSymbols method
ms.assetid: 0f9f0133-7d58-4cd9-a6ca-1141e095749d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 20a3d7715e3dacac1e7e64e5d52434e48615e7e2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757882"
---
# <a name="idebugmodule2reloadsymbolsdeprecated"></a>IDebugModule2::ReloadSymbols_Deprecated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

사용되지 않습니다. 사용 하지 마세요. 이 모듈의 기호를 다시 로드합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
HRESULT ReloadSymbols(   
   LPCOLESTR pszUrlToSymbols,  
   BSTR*     pbstrDebugMessage  
);  
```  
  
```csharp  
int ReloadSymbols(   
   string     pszUrlToSymbols,  
   out string pbstrDebugMessage  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszUrlToSymbols`  
 [in] 기호 저장소에 대 한 경로입니다.  
  
 `pbstrDebugMessage`  
 [out] 모듈 창에서 모듈 이름 오른쪽에 표시 되는 상태 또는 오류 메시지와 같은 정보 메시지를 반환 합니다.  
  
## <a name="return-value"></a>반환 값  
 성공 하면 반환 `S_OK`고, 그렇지 않으면 오류 코드를 반환 합니다. 디버그 엔진을 항상 반환 `E_FAIL`합니다.  
  
## <a name="remarks"></a>설명  
 이 메서드는 더 이상 지원 합니다. 구현 된 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md) 메서드 대신 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)

