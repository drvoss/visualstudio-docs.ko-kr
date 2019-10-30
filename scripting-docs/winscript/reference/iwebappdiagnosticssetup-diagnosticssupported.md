---
title: IWebAppDiagnosticsSetup::D iagnosticsSupported | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd27e7c8759054fa2d7d67858d8d006fa9c9a152
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984579"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
이 응용 프로그램에서 진단이 지원 되는지 여부를 확인 합니다. NULL이 아닌 값을 사용 하 여이 인터페이스를 구현 하는 개체에서 [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) 가 호출 된 경우 [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) 는 `true`을 반환 합니다. 그렇지 않으면 `false`을 반환 하 고 [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) 에 대 한 호출이 실패 합니다.  
  
> [!IMPORTANT]
> [IWebAppDiagnosticsSetup 인터페이스](../../winscript/reference/iwebappdiagnosticssetup-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. Activdbg100.h에서 찾았습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pRetVal`  
 NULL이 아닌 값을 사용 하 여이 인터페이스를 구현 하는 개체에서 [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) 가 호출 된 경우 [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) 는 `true`을 반환 합니다. 그렇지 않으면 `false`을 반환 하 고 [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) 에 대 한 호출이 실패 합니다.