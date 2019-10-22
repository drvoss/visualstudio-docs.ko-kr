---
title: ISimpleConnectionPoint 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ISimpleConnectionPoint interface
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549d7f38b01937f992b240cb6f1d651bc848236c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571794"
---
# <a name="isimpleconnectionpoint-interface"></a>ISimpleConnectionPoint 인터페이스
특정 연결 지점에서 발생 하는 이벤트를 설명 하 고 열거 하는 간단한 방법을 제공 합니다. 이 인터페이스를 사용 하면 `IDispatch` 개체를 이러한 이벤트에 쉽게 연결할 수 있습니다. 이 인터페이스는 프로세스 디버그 관리자 (PDM)에서 구현 되며 스크립트 엔진에서 사용 됩니다.  
  
 이 인터페이스는 `IDebugHelper::CreateSimpleConnectionPoint`에서 사용할 수 있습니다.  
  
 @No__t_0에서 상속 된 메서드 외에도 `ISimpleConnectionPoint` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|단순 연결 지점 개체와 클라이언트의 싱크 간에 연결을 설정 합니다.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|지정 된 이벤트 범위에서 각 이벤트에 대 한 DISPID 및 이름을 반환 합니다.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|이 인터페이스에 노출 되는 이벤트 수를 반환 합니다.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|@No__t_0를 통해 이전에 설정 된 advise 연결을 종료 합니다.|  
  
## <a name="see-also"></a>참조  
 [IDebugProperty 인터페이스](../../winscript/reference/idebugproperty-interface.md)