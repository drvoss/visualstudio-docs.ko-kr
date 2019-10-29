---
title: 'IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 253b995c200566868ac9ccc06b259e0a152e1676
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984602"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
이 메서드는 `dwClsContext`를 사용 하 여 `rclsid`에 전달 하는 ID를 가진 클래스를 공동으로 만듭니다. 이는 `CreateObjectWithSiteAtWebApp`의 경우 웹 응용 프로그램의 UI 스레드에서 비동기적으로 개체를 만드는 경우를 제외 하 고는 [Iremotedebugapplication:: CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) works와 비슷합니다. 클래스 ID로 지정 된 개체는 [IWebAppDiagnosticsObjectInitialization 인터페이스](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)를 구현 해야 합니다. 개체를 만든 후에는 PDM 디버그 응용 프로그램에 대 한 참조 및 `CreateObjectWithSiteAtWebApp`의 `hPassToObject` 매개 변수를 사용 하 여 [IWebAppDiagnosticsObjectInitialization:: Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) 가 호출 됩니다. 이 메서드를 사용 하 여 [DuplicateHandle](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle)를 사용 하 여 복사한 익명 파이프에 대 한 핸들을 앱에 전달할 수 있습니다.  
  
> [!IMPORTANT]
> [IWebAppDiagnosticsSetup 인터페이스](../../winscript/reference/iwebappdiagnosticssetup-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>매개 변수  
 `rclsid`  
 만들 클래스의 클래스 ID입니다.  
  
 `dwClsContext`  
 코드가 실행 될 컨텍스트입니다. 대부분의 경우에는 CLSCTX_INPROC_SERVER입니다.  
  
 `riid`  
 사용되지 않습니다.  
  
 `hPassToObject`  
 개체가 [IWebAppDiagnosticsObjectInitialization 인터페이스](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)를 구현 하는 경우 UI 스레드에서 만들어진 후 개체에 전달 되는 값입니다.