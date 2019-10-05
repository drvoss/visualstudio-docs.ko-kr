---
title: IDebugDocumentHelper 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentHelper interface
ms.assetid: b652a31e-b87b-45f1-b586-94f2b6e822db
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7322ea5e2026ff3f4491ed1106dceb97a5f11c73
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63000907"
---
# <a name="idebugdocumenthelper-interface"></a>IDebugDocumentHelper 인터페이스
와 같은 스마트 호스팅에 필요한 많은 인터페이스에 대 한 구현을 제공 합니다 `IDebugDocument`, `IDebugDocumentContext`를 `IDebugDocumentProvider`, `IDebugDocumentText`, 및 `IDebugDocumentTextEvents` 인터페이스입니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IDebugDocumentHelper` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugDocumentHelper::Init](../../winscript/reference/idebugdocumenthelper-init.md)|이름과 초기 특성을 사용 하 여 디버그 문서 도우미를 초기화합니다.|  
|[IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)|문서 트리에서이 문서에 추가 합니다.|  
|[IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)|문서 트리에서이 문서를 제거합니다.|  
|[IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)|종료 유니코드 문자열을 추가 합니다.이 문서의.|  
|[IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)|DBCS 문자열 끝을 추가 합니다.이 문서의.|  
|[IDebugDocumentHelper::SetDebugDocumentHost](../../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md)|집합의 `IDebugDocumentHost` 이 문서에 대 한 합니다.|  
|[IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)|지정된 된 텍스트를 사용할 수 있지만 문자를 제공 하지 않으며 도우미에 알립니다.|  
|[IDebugDocumentHelper::DefineScriptBlock](../../winscript/reference/idebugdocumenthelper-definescriptblock.md)|특정 범위의 문자는 스크립트 블록 지정 된 스크립트 엔진에서 처리 하는 도우미를 나타냅니다.|  
|[IDebugDocumentHelper::SetDefaultTextAttr](../../winscript/reference/idebugdocumenthelper-setdefaulttextattr.md)|스크립트 블록에 없는 텍스트에 사용할 기본 특성을 설정 합니다.|  
|[IDebugDocumentHelper::SetTextAttributes](../../winscript/reference/idebugdocumenthelper-settextattributes.md)|텍스트 범위에 특성을 설정합니다.|  
|[IDebugDocumentHelper::SetLongName](../../winscript/reference/idebugdocumenthelper-setlongname.md)|문서에 대 한 긴 이름을 설정합니다.|  
|[IDebugDocumentHelper::SetShortName](../../winscript/reference/idebugdocumenthelper-setshortname.md)|문서에 대 한 짧은 이름을 설정합니다.|  
|[IDebugDocumentHelper::SetDocumentAttr](../../winscript/reference/idebugdocumenthelper-setdocumentattr.md)|이 문서에 대 한 특성을 설정합니다.|  
|[IDebugDocumentHelper::GetDebugApplicationNode](../../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)|이 문서에 해당 하는 디버그 응용 프로그램 노드를 반환 합니다.|  
|[IDebugDocumentHelper::GetScriptBlockInfo](../../winscript/reference/idebugdocumenthelper-getscriptblockinfo.md)|문자 및 스크립트 엔진에 해당 하는 스크립트 블록의 범위를 검색 합니다.|  
|[IDebugDocumentHelper::CreateDebugDocumentContext](../../winscript/reference/idebugdocumenthelper-createdebugdocumentcontext.md)|새 디버그 문서 컨텍스트를 만듭니다.|  
|[IDebugDocumentHelper::BringDocumentToTop](../../winscript/reference/idebugdocumenthelper-bringdocumenttotop.md)|사용자 인터페이스는 디버거에서 맨 위로 이동이 문서의 제공합니다.|  
|[IDebugDocumentHelper::BringDocumentContextToTop](../../winscript/reference/idebugdocumenthelper-bringdocumentcontexttotop.md)|디버거 사용자 인터페이스에서 위쪽에이 문서의 컨텍스트를 제공합니다.|