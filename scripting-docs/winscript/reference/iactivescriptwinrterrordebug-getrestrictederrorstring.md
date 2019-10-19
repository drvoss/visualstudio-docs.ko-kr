---
title: 'IActiveScriptWinRTErrorDebug:: GetRestrictedErrorString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
ms.assetid: d901e049-fb1b-4101-a04a-1395d657f1cf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 498d929fb06eea1d6717bfdecb09107bbdaafd98
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577899"
---
# <a name="iactivescriptwinrterrordebuggetrestrictederrorstring"></a>IActiveScriptWinRTErrorDebug::GetRestrictedErrorString
사용 가능한 경우 Windows 런타임 제한 된 오류 문자열을 반환 합니다.  
  
> [!IMPORTANT]
> [IActiveScriptWinRTErrorDebug 인터페이스](../../winscript/reference/iactivescriptwinrterrordebug-interface.md) 는 PDM v 11.0 이상에 의해 구현 됩니다. activdbg100.h에서 찾을 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
HRESULT GetRestrictedErrorString([out] BSTR * errorString);   
```  
  
#### <a name="parameters"></a>매개 변수  
 `errorString`  
 제한이 제한 된 오류 문자열입니다.  
  
## <a name="see-also"></a>참조  
 [IActiveScriptWinRTErrorDebug 인터페이스](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)