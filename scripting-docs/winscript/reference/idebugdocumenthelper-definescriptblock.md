---
title: IDebugDocumentHelper::D efineScriptBlock | Microsoft Docs
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
ms.openlocfilehash: 6a2418b18e80ac86b672b3847f24ef9084ed1252
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576984"
---
# <a name="idebugdocumenthelperdefinescriptblock"></a>IDebugDocumentHelper::DefineScriptBlock
도우미에 특정 문자 범위가 지정 된 스크립트 엔진에서 처리 하는 스크립트 블록 임을 나타냅니다.  
  
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
 진행 스크립트 블록의 시작 위치입니다.  
  
 `cChars`  
 진행 스크립트 블록의 문자 수입니다.  
  
 `pas`  
 진행 이 스크립트 블록에 대 한 스크립트 엔진입니다.  
  
 `fScriptlet`  
 진행 스크립트 블록이 scriptlet 여부를 나타내는 플래그입니다.  
  
 `pdwSourceContext`  
 제한이 스크립트 블록의 소스 컨텍스트입니다.  
  
## <a name="return-value"></a>반환 값  
 이 메서드는 `HRESULT`를 반환합니다. 가능한 값에는 다음 표에 있는 값이 포함되지만, 이에 국한되는 것은 아닙니다.  
  
|값|설명|  
|-----------|-----------------|  
|`S_OK`|메서드가 성공했으며|  
  
## <a name="remarks"></a>주의  
 스마트 호스트는 문서에 포함 된 스크립트 블록이 포함 된 경우이 메서드를 사용할 수 있습니다. 언어 엔진은 해당 코드에 다른 언어에 대 한 포함 스크립트를 포함 하는 경우이 메서드를 사용할 수 있습니다.  
  
 스크립트 엔진은 스크립트 블록의 모든 구문 색 지정 및 코드 컨텍스트 조회를 담당 합니다.  
  
 `DefineScriptBlock` 메서드는 텍스트가 추가 된 후 (예: `IDebugDocumentHelper::AddDBCSText` 메서드 사용) 스크립트 블록이 구문 분석 되기 전에 호출 해야 합니다 (예: `IActiveScriptParse ::ParseScriptText` 메서드 사용).  
  
## <a name="see-also"></a>참고 항목  
 [IDebugDocumentHelper 인터페이스](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)