---
title: IDebugDocumentContext 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentContext interface
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df4c8b8639a6d4b232f82cf87fff7b069829cc46
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62783196"
---
# <a name="idebugdocumentcontext-interface"></a>IDebugDocumentContext 인터페이스
디버그 중인 문서의 일부에 대한 추상 표현을 제공합니다. 텍스트 문서에 대 한이 표현은 문자 위치 범위의 구성 됩니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IDebugDocumentContext` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|이 컨텍스트를 포함 하는 문서를 반환 합니다.|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|이 문서 컨텍스트와 연결 된 코드 컨텍스트 열거 합니다.|