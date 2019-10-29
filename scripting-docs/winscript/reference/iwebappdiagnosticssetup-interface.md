---
title: IWebAppDiagnosticsSetup 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9bb3905da6227b978bc27b96493500f8d6d2ff
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984535"
---
# <a name="iwebappdiagnosticssetup-interface"></a>IWebAppDiagnosticsSetup 인터페이스
이 인터페이스는 디버깅 중인 프로세스에서 COM 개체를 만들고 웹 진단을 사용 하도록 설정 하기 위해 PDM 디버그 응용 프로그램에 의해 구현 됩니다. PDM 디버그 응용 프로그램 개체가 [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite)을 구현 하는 경우 Internet Explorer는 생성 된 후 [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) 를 호출 하 고 [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127(v=vs.85))에 대 한 참조를 전달 합니다. WWA 응용 프로그램은 [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) 를 호출 하 고, 대신 wwa 인터페이스 IWebApplicationHost를 전달 합니다. NULL이 아닌 값을 사용 하 여 [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) 를 호출 하면 [IWebAppDiagnosticsSetup::D iagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) 가 true를 반환 합니다. 그렇지 않으면 false를 반환 하 고 [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) 에 대 한 호출이 실패 합니다.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup`는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="methods"></a>메서드  
 이 인터페이스는 다음 메서드를 노출 합니다.  
  
|메서드|설명|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|지정 된 필터에 의해 숨겨진 텍스트 문서를 가져옵니다.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|지정 된 문서가이 노드의 자식 노드 중 하나에 속하는지 여부를 확인 합니다.|