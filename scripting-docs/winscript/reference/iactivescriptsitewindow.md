---
title: IActiveScriptSiteWindow | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteWindow interface
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ee680a3d00c6736549b03ce8fee5593a7a8c5af
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575900"
---
# <a name="iactivescriptsitewindow"></a>IActiveScriptSiteWindow
이 인터페이스는 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 와 동일한 개체의 사용자 인터페이스를 지 원하는 호스트에 의해 구현 됩니다. 서버와 같은 사용자 인터페이스를 지원 하지 않는 호스트는 `IActiveScriptSiteWindow` 인터페이스를 구현 하지 않습니다. 스크립팅 엔진은 `IActiveScriptSite`에서 `QueryInterface`를 호출 하 여이 인터페이스에 액세스 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|스크립팅 엔진에서 표시 해야 하는 팝업 창의 소유자 역할을 할 수 있는 창 핸들을 검색 합니다.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|호스트에서 주 창 및 모덜리스 대화 상자를 사용 하거나 사용 하지 않도록 설정 합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 인터페이스](../../winscript/reference/active-script-interfaces.md)