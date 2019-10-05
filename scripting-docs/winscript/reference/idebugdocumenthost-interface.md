---
title: IDebugDocumentHost 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHost interface
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 226e2700b471cd34496682d233e57946e124ff3b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62939226"
---
# <a name="idebugdocumenthost-interface"></a>IDebugDocumentHost 인터페이스
구문 색 지정, 디버거 같은 호스트 관련 기능을 노출 합니다. `IDebugDocumentHelper::SetDebugDocumentHost` 메서드 인수로이 인터페이스를 사용 합니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IDebugDocumentHost` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|사용 하 여 추가 된 문자의 범위를 반환 `IDebugDocumentHelper::AddDeferredText`, 원래 호스트 문서에서.|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|문서 텍스트 블록에 대 한 텍스트 특성을 반환합니다.|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|새 문서 컨텍스트를 만들고 있는 중 이며, 호스트가 필요에 따라 새 컨텍스트를 제어 하는 개체를 반환할 수 있도록 호스트에 알립니다.|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|문서의 소스 파일의 전체 경로 (파일 이름 포함)를 반환 합니다.|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|경로 정보 없이 문서의 이름을 반환합니다.|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|문서의 소스 파일을 저장 하 고 해당 내용을 새로 고쳐져 야 하는 호스트에 알립니다.|