---
title: 'Idebugdocumenthelper:: Definescriptblock | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHelper.DefineScriptBlock
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentHelper::DefineScriptBlock
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a320e4e43a983ace4decbaa68de0b1a7df7d457
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783026"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
도우미 특정 문자 범위 지정 된 스크립트 엔진에서 처리 되는 스크립트 블록을 임을 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `ulCharOffset`  
 [in] 스크립트 블록의 시작 위치입니다.  
  
 `cChars`  
 [in] 스크립트 블록의 문자 수입니다.  
  
 `pas`  
 [in] 이 스크립트 블록에 대 한 스크립트 엔진입니다.  
  
 `fScriptlet`  
 [in] 스크립트 블록을 scriptlet 인지를 나타내는 플래그입니다.  
  
 `pdwSourceContext`  
 [out] 스크립트 블록의 소스 컨텍스트입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>설명  
 스마트 호스트는 해당 문서가 포함 된 스크립트 블록을 포함 하는 경우이 메서드를 사용할 수 있습니다. 언어 엔진을 해당 코드는 다른 언어에 대 한 포함 된 스크립트를 포함 하는 경우이 메서드를 사용할 수 있습니다.  
  
 스크립트 엔진이 스크립트 블록의 모든 구문 색 지정 및 코드 컨텍스트 조회 담당합니다.  
  
 합니다 `DefineScriptBlock` 텍스트를 추가한 다음 메서드를 호출 해야 (예를 들어,를 사용 하 여는 `IDebugDocumentHelper::AddDBCSText` 메서드) 전에 스크립트 블록을 구문 분석 된가 있지만 (예를 들어,를 사용 하 여를 `IActiveScriptParse ::ParseScriptText` 메서드).  
  
## <a name="see-also"></a>참고 항목  
 [IDebugDocumentHelper 인터페이스](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)