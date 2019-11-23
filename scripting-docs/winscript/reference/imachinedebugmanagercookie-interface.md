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
ms.openlocfilehash: 6b39c286f389c99187b0f3250fc68af92ff5dcc8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573880"
---
# <a name="imachinedebugmanagercookie-interface"></a>IMachineDebugManagerCookie 인터페이스
`IMachineDebugManager` 인터페이스와 마찬가지로 `IMachineDebugManagerCookie` 인터페이스는 디버그 쿠키를 지원 합니다.  
  
 이 인터페이스 (`IDebugCookie` 인터페이스와 함께)를 사용 하면 디버거가 스크립트를 추적 하지 않아도 스크립트 디버거 프로세스에서 스크립트를 실행할 수 있습니다.  
  
 스크립트 디버거는 PDM (프로세스 디버그 관리자)에서 `IDebugCookie::SetDebugCookie` 메서드를 호출 합니다. 그러면 PDM은 `IMachineDebugManagerCookie` 인터페이스의 메서드를 사용 하 여이 쿠키를 MDM (컴퓨터 디버그 관리자)에 추가 하거나 제거 하는 요청과 함께이 쿠키를 보냅니다. 그러면 MDM은 해당 쿠키를 포함 하는 것을 제외 하 고 모든 디버거에 변경 내용을 알립니다.  
  
 `IUnknown`에서 상속 된 메서드 외에도 `IMachineDebugManagerCookie` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IMachineDebugManagerCookie::AddApplication](../../winscript/reference/imachinedebugmanagercookie-addapplication.md)|응용 프로그램을 실행 중인 응용 프로그램 목록에 추가 합니다.|  
|[IMachineDebugManagerCookie::EnumApplications](../../winscript/reference/imachinedebugmanagercookie-enumapplications.md)|실행 중인 응용 프로그램의 현재 목록에 대 한 열거자를 반환 합니다.|  
|[IMachineDebugManagerCookie::RemoveApplication](../../winscript/reference/imachinedebugmanagercookie-removeapplication.md)|응용 프로그램을 실행 중인 응용 프로그램 목록에서 제거 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Imach  Debugmanager 인터페이스](../../winscript/reference/imachinedebugmanager-interface.md)  
 [IDebugCookie 인터페이스](../../winscript/reference/idebugcookie-interface.md)