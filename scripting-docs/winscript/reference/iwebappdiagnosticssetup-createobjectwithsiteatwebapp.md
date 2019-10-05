---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Microsoft Docs
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
ms.openlocfilehash: 42f92cfe9245a5e3a6342c31fc996ae2db50ef70
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443704"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
이 메서드는 클래스에 전달 하면 해당 ID를 만듭니다 공동 `rclsid` 를 사용 하는 `dwClsContext`합니다. 이 방식과 유사 하 게 [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) 의 경우는 제외 하 고 작동 `CreateObjectWithSiteAtWebApp` 개체는 웹 응용 프로그램의 UI 스레드에서 비동기적으로 생성 됩니다. 클래스 ID에서 지정한 개체를 구현 해야 [IWebAppDiagnosticsObjectInitialization 인터페이스](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)합니다. 개체를 만든 후 [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) PDM 디버그 응용 프로그램에 대 한 참조를 사용 하 여 라고 하며 `hPassToObject` 의 매개 변수 `CreateObjectWithSiteAtWebApp`합니다. 이 메서드를 사용 하 여 전달할 앱에 대 한 핸들을 사용 하 여 복사 된 익명 파이프 [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450)합니다.  
  
> [!IMPORTANT]
> [IWebAppDiagnosticsSetup 인터페이스](../../winscript/reference/iwebappdiagnosticssetup-interface.md) 는 PDM v11.0에 의해 구현 된 이상. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>매개 변수  
 `rclsid`  
 만들 클래스의 클래스 ID입니다.  
  
 `dwClsContext`  
 코드가 실행 되는 컨텍스트입니다. 대부분의 경우에서 CLSCTX_INPROC_SERVER 것입니다.  
  
 `riid`  
 사용되지 않습니다.  
  
 `hPassToObject`  
 전달 되는 개체를 UI 스레드에서 만들어진 후 개체를 구현 하는 경우 값 [IWebAppDiagnosticsObjectInitialization 인터페이스](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)합니다.