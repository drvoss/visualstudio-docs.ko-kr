---
title: IDebugDocumentTextEvents 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c83a6e3a41ed7087338989d5cb077fa070e724b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434260"
---
# <a name="idebugdocumenttextevents-interface"></a>IDebugDocumentTextEvents 인터페이스
관련 텍스트 문서의 변경 내용을 나타내는 이벤트를 제공합니다.  
  
> [!NOTE]
> 문서 텍스트에는이 이벤트 인터페이스 발생 하는 경우 변경 합니다. 이벤트 처리기를 사용 하 여 새 텍스트를 검색할 수 있습니다는 `IDebugDocumentText` 인터페이스입니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IDebugDocumentTextEvents` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|기본 문서 소멸 된 더 이상 유효 하지 나타냅니다.|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|새 텍스트 문서에 추가 된 것을 나타냅니다.|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|텍스트 문서에서 제거 된 것을 나타냅니다.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|텍스트를 교체한 나타냅니다.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|기본 문자 위치 범위의 연관 된 텍스트 특성 변경 되었다는 것을 나타냅니다.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|문서 속성 변경 되었음을 나타냅니다.|