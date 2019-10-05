---
title: IActiveScriptSite | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67e16e2825f03c9ae452e639d6a086bee584ac95
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992562"
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Windows 스크립트 엔진에 대 한 사이트를 만들려면 호스트에서 구현 합니다. 일반적으로이 사이트 (예를 들어, ActiveX 컨트롤) 스크립트에 표시 되는 모든 개체의 컨테이너와 연결 됩니다. 일반적으로이 컨테이너는 문서 또는 표시 되는 페이지에 대응 됩니다. 예를 들어 Microsoft Internet Explorer에 표시 되 고 각 HTML 페이지에 대 한 이러한 컨테이너를 만들어집니다. 각 ActiveX 컨트롤 (또는 다른 자동화 개체) 스크립팅 엔진 자체 페이지에는이 컨테이너에 있는 열거 가능한 것입니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|||  
|-|-|  
|메서드|설명|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|사용자 인터페이스 요소를 표시 하는 것에 대 한 호스트를 사용 하는 로캘 식별자를 검색 합니다.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|호출 하 여 엔진에 추가 된 항목에 대 한 정보를 가져오고 합니다 [iactivescript:: Addnameditem](../../winscript/reference/iactivescript-addnameditem.md) 메서드.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|고유 하 게 호스트의 관점에서 현재 문서 버전을 식별 하는 호스트 정의 문자열을 검색 합니다.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|스크립트 실행이 완료 될 때 호출 됩니다.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|스크립팅 엔진 상태 데이터가 변경 되었음을 호스트에 알립니다.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|엔진을 스크립트를 실행 하는 동안 실행 오류가 발생 했음을 호스트에 알립니다.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|스크립팅 엔진에 스크립트 코드를 실행 했음을 호스트에 알립니다.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|스크립트 코드를 실행 스크립팅 엔진에 반환 되는 호스트에 알립니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 인터페이스](../../winscript/reference/active-script-interfaces.md)