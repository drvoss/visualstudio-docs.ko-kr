---
title: IDebugApplicationNodeEvents 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNodeEvents interface
ms.assetid: 02e0bb17-84ce-458b-bae6-608a9899e535
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a2f72290e331a51f1b33746b22a6526c9bfbac7b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574712"
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents 인터페이스
`IDebugApplicationNode` 인터페이스에 대한 이벤트 인터페이스를 제공합니다.  
  
 @No__t_0에서 상속 된 메서드 외에도 `IDebugApplicationNodeEvents` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|자식 노드가 디버그 응용 프로그램 노드 개체에 추가 될 때 이벤트를 처리 합니다.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|디버그 응용 프로그램 노드 개체에서 자식 노드를 제거할 때 이벤트를 처리 합니다.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|디버그 응용 프로그램 노드 개체가 부모 노드에서 분리 되었음을 나타내는 이벤트를 처리 합니다.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|디버그 응용 프로그램 노드 개체가 부모 노드에 연결 되었음을 나타내는 이벤트를 처리 합니다.|  
  
## <a name="see-also"></a>참조  
 [IDebugApplicationNode 인터페이스](../../winscript/reference/idebugapplicationnode-interface.md)