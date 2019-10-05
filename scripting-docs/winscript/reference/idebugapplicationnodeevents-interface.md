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
ms.openlocfilehash: 7412e258c7f67f44bde6f69b593a1eecb1d84e07
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822277"
---
# <a name="idebugapplicationnodeevents-interface"></a>IDebugApplicationNodeEvents 인터페이스
`IDebugApplicationNode` 인터페이스에 대한 이벤트 인터페이스를 제공합니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IDebugApplicationNodeEvents` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IDebugApplicationNodeEvents::onAddChild](../../winscript/reference/idebugapplicationnodeevents-onaddchild.md)|자식 노드를 디버그 하는 응용 프로그램 노드 개체를 추가할 때 이벤트를 처리 합니다.|  
|[IDebugApplicationNodeEvents::onRemoveChild](../../winscript/reference/idebugapplicationnodeevents-onremovechild.md)|디버그 응용 프로그램 노드 개체의 자식 노드를 제거할 때 이벤트를 처리 합니다.|  
|[IDebugApplicationNodeEvents::onDetach](../../winscript/reference/idebugapplicationnodeevents-ondetach.md)|부모 노드에서 디버그 응용 프로그램 노드 개체를 분리할를 나타내는 이벤트를 처리 합니다.|  
|[IDebugApplicationNodeEvents::onAttach](../../winscript/reference/idebugapplicationnodeevents-onattach.md)|디버그 응용 프로그램 노드 개체 부모 노드에 연결 된 있는지를 나타내는 이벤트를 처리 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [IDebugApplicationNode 인터페이스](../../winscript/reference/idebugapplicationnode-interface.md)