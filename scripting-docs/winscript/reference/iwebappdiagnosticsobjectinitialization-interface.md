---
title: IWebAppDiagnosticsObjectInitialization 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization Interface
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a992f8512d4927eeb58d6437ccb830abda688b28
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443691"
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>IWebAppDiagnosticsObjectInitialization 인터페이스
이 인터페이스를 구현 하는 클래스에서 구현할 수 있습니다 [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)합니다. [IWebAppDiagnosticsSetup 인터페이스](../../winscript/reference/iwebappdiagnosticssetup-interface.md) 구현 하는 개체에 의해 구현 됩니다 [IDebugApplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)합니다. 대부분의 경우가이 개체는 PDM입니다.  
  
 개체를 만든 후 [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) PDM 디버그 응용 프로그램에 대 한 참조를 사용 하 여 라고 하며 `hPassToObject` 의 매개 변수 `CreateObjectWithSiteAtWebApp`합니다.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsObjectInitialization` activdbg100.h에서 발견 됩니다.  
  
## <a name="methods"></a>메서드  
 이 인터페이스는 다음 메서드를 노출 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|개체를 초기화합니다.|