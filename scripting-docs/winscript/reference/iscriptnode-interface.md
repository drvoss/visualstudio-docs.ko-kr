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
ms.openlocfilehash: 38ab73ddb1bd924035cb6ba61d26e65f16f53eed
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577511"
---
# <a name="iscriptnode-interface"></a>IScriptNode 인터페이스
@No__t_0 인터페이스를 구현 하는 개체는 웹 페이지를 나타냅니다.  
  
 @No__t_0에서 상속 된 메서드 외에도 `IScriptNode` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IScriptNode::Alive](../../winscript/reference/iscriptnode-alive.md)|개체가 여전히 활성 상태 인지 여부를 나타냅니다.|  
|[IScriptNode:: CreateChildEntry](../../winscript/reference/iscriptnode-createchildentry.md)|@No__t_0의 자식 인스턴스를 추가 합니다.|  
|[IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md)|Scriptlet를 `IScriptNode`의 자식 인스턴스로 추가 합니다.|  
|[IScriptNode::Delete](../../winscript/reference/iscriptnode-delete.md)|개체 트리를 삭제 합니다.|  
|[IScriptNode::GetChild](../../winscript/reference/iscriptnode-getchild.md)|노드의 지정 된 인덱스에 있는 자식을 반환 합니다.|  
|[IScriptNode::GetCookie](../../winscript/reference/iscriptnode-getcookie.md)|Scriptlet을 호스트 개체와 연결 하는 데 사용 되는 응용 프로그램 정의 값을 반환 합니다.|  
|[IScriptNode::GetIndexInParent](../../winscript/reference/iscriptnode-getindexinparent.md)|부모의 자식 목록에 있는 개체의 인덱스를 반환 합니다.|  
|[IScriptNode::GetLanguage](../../winscript/reference/iscriptnode-getlanguage.md)|현재 스크립트 노드에서 사용 하는 스크립트 언어를 반환 합니다.|  
|[IScriptNode::GetNumberOfChildren](../../winscript/reference/iscriptnode-getnumberofchildren.md)|@No__t_0 개체의 자식 노드 수를 반환 합니다.|  
|[IScriptNode::GetParent](../../winscript/reference/iscriptnode-getparent.md)|개체의 부모인 `IScriptNode` 개체를 반환 합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 작성 인터페이스](../../winscript/reference/active-script-authoring-interfaces.md)