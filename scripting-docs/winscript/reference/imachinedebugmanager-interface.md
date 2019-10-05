---
title: IMachineDebugManager 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IMachineDebugManager interface
ms.assetid: 0b7133bb-5a52-4036-b4db-d69260790db7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6db8989fc6c932723a9b95017854635396b0deda
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977645"
---
# <a name="imachinedebugmanager-interface"></a>IMachineDebugManager 인터페이스
컴퓨터 디버그 관리자에 게 기본 인터페이스입니다. 이 인터페이스는 비슷합니다는 `IMachineDebugManagerCookie` 인터페이스입니다.  
  
 상속 된 메서드 외에도 `IUnknown`, `IMachineDebugManager` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IMachineDebugManager::AddApplication](../../winscript/reference/imachinedebugmanager-addapplication.md)|응용 프로그램을 실행 하는 추가 응용 프로그램 목록입니다.|  
|[IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)|실행 중인 응용 프로그램을 제거 합니다. 응용 프로그램 목록입니다.|  
|[IMachineDebugManager::EnumApplications](../../winscript/reference/imachinedebugmanager-enumapplications.md)|현재 실행 중인 응용 프로그램 목록의 열거자를 반환 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [IMachineDebugManagerCookie 인터페이스](../../winscript/reference/imachinedebugmanagercookie-interface.md)