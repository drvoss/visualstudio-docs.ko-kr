---
title: IDebugDocumentText 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentText interface
ms.assetid: 242bad79-9c0a-4a30-879a-9f43db4e022b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8878e1ce6e9ad05fc94b134a2e71847b67d578d2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63008617"
---
# <a name="idebugdocumenttext-interface"></a>IDebugDocumentText 인터페이스
디버그 문서의 텍스트 전용 버전에 대한 액세스를 제공합니다. 이 인터페이스는 다음 규칙을 사용 합니다.  
  
- 문자 위치 및 줄 번호는 0부터 시작 합니다.  
  
- 문자 위치 나타내는 문자 오프셋입니다. 바이트를 나타내는 또는 단어 오프셋 아닙니다. Win32의 문자 위치는는 유니코드 오프셋입니다.  
  
  상속 된 메서드 외에도 `IDebugDocument`, `IDebugDocumentText` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugDocumentText::GetDocumentAttributes](../../winscript/reference/idebugdocumenttext-getdocumentattributes.md)|문서의 특성을 반환 합니다.|  
|[IDebugDocumentText::GetSize](../../winscript/reference/idebugdocumenttext-getsize.md)|문서의 줄 번호 및 문자 수를 반환합니다.|  
|[IDebugDocumentText::GetPositionOfLine](../../winscript/reference/idebugdocumenttext-getpositionofline.md)|문자 위치에 해당 줄의 첫 번째 문자를 반환 합니다.|  
|[IDebugDocumentText::GetLineOfPosition](../../winscript/reference/idebugdocumenttext-getlineofposition.md)|지정된 된 문자 위치에 줄 번호 및 필요에 따라 해당 하는 줄 내 문자 오프셋을 반환 합니다.|  
|[IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)|문자 및/또는 연결 된 문자 위치 범위의 문자 특성을 검색 합니다.|  
|[IDebugDocumentText::GetPositionOfContext](../../winscript/reference/idebugdocumenttext-getpositionofcontext.md)|문서 컨텍스트에 해당 하는 문자 위치 범위를 반환 합니다.|  
|[IDebugDocumentText::GetContextOfPosition](../../winscript/reference/idebugdocumenttext-getcontextofposition.md)|제공 된 문자 위치 범위에 해당 하는 문서 컨텍스트 개체를 만듭니다.|