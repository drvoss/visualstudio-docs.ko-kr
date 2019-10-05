---
title: IMachineDebugManagerCookie 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManagerCookie interface
ms.assetid: 04770935-3ccf-41e9-b0c1-c78376ab1e3c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fdc02498360f2e3900012166474c5d1e35abd6ee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977686"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie 인터페이스
비슷합니다는 `IMachineDebugManager` 인터페이스는 `IMachineDebugManagerCookie` 인터페이스에서 디버그 쿠키를 지원 합니다.  
  
 이 인터페이스 (함께 `IDebugCookie` 인터페이스) 스크립트를 스크립트 디버거 프로세스에서 디버거는 해당 스크립트에서의 추적 유지 하지 않고도 실행할 수 있습니다.  
  
 스크립트 디버거를 호출 합니다 `IDebugCookie::SetDebugCookie` 메서드 프로세스 디버그 관리자 (PDM)에 있습니다. 그런 다음 PDM이이 쿠키를 추가 하 여 스크립트 응용 프로그램을 제거 하거나에서 컴퓨터 디버그 관리자 (MDM), 모든 요청과 함께 사용 하 여 보냅니다의 메서드는 `IMachineDebugManagerCookie` 인터페이스입니다. MDM을 제외 하 고 해당 쿠키에 있는 변경의 모든 디버거를 알립니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IMachineDebugManagerCookie` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|응용 프로그램을 실행 하는 추가 응용 프로그램 목록입니다.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|현재 실행 중인 응용 프로그램 목록의 열거자를 반환 합니다.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|실행 중인 응용 프로그램을 제거 합니다. 응용 프로그램 목록입니다.|  
  
## <a name="see-also"></a>참고 항목  
 [IMachineDebugManager 인터페이스](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IDebugCookie 인터페이스](../../winscript/reference/idebugcookie-interface.md)