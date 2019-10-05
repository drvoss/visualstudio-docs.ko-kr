---
title: IScriptNode 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IScriptNode interface
ms.assetid: cfa76c4a-6543-48e8-a946-d212cd0bf934
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13bf20f9e1e642b948ddaa72ae9dca7bb457fba2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786776"
---
# <a name="iscriptnode-interface"></a>IScriptNode 인터페이스
구현 하는 개체는 `IScriptNode` 인터페이스 웹 페이지를 나타냅니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IScriptNode` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|개체가 아직 활성 인지를 나타냅니다.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|자식 인스턴스 추가 `IScriptEntry`합니다.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|자식 인스턴스는 scriptlet 추가 `IScriptNode`합니다.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|개체 트리를 삭제합니다.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|노드에 지정된 된 인덱스에 있는 자식을 반환 합니다.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|호스트 개체를 사용 하 여 scriptlet을 연결 하는 데 사용 되는 응용 프로그램 정의 값을 반환 합니다.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|부모의 자식 목록에 있는 개체의 인덱스를 반환합니다.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|현재 스크립트 노드에 의해 사용 되는 스크립트 언어를 반환 합니다.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|자식 노드의 수를 반환 합니다 `IScriptNode` 개체입니다.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|반환 된 `IScriptNode` 개체의 부모인 개체입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 작성 인터페이스](../../winscript/reference/active-script-authoring-interfaces.md)