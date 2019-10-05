---
title: IDebugApplicationNode 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode interface
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9be864fdb9468668633322066bbbcf11569e4eb3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822427"
---
# <a name="idebugapplicationnode-interface"></a>IDebugApplicationNode 인터페이스
합니다 `IDebugApplicationNode` 인터페이스의 기능을 확장 합니다 `IDebugDocumentProvider` 프로젝트 트리 내에서 컨텍스트를 제공 하 여 인터페이스입니다.  
  
 상속 된 메서드 외에도 `IDebugDocumentProvider`, `IDebugApplicationNode` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|이 응용 프로그램 노드의 자식 노드를 열거합니다.|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|이 응용 프로그램 노드의 부모 노드를 반환합니다.|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|이 응용 프로그램 노드에 대 한 문서 공급자를 설정 합니다.|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|이 응용 프로그램을 모든 참조를 해제 하 고 비활성 상태가 발생 합니다.|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|지정한 프로젝트 트리에이 응용 프로그램 노드를 추가합니다.|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|프로젝트 트리에서이 응용 프로그램 노드를 제거합니다.|