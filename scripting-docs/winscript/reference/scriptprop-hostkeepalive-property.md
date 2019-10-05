---
title: SCRIPTPROP_HOSTKEEPALIVE 속성 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724bfcb1ec42617cda4c89269cb0160accafb1a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840346"
---
# <a name="scriptprophostkeepalive-property"></a>SCRIPTPROP_HOSTKEEPALIVE 속성
지정 여부 스크립팅 엔진은 유지 해야 처리 중인 참조가 있는 경우에 완벽 하 게 작동 하는 데 사용 합니다.  
  
 사용 하 여 [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) 이 속성을 설정 하려면 `true`합니다. 이 속성 설정 된 경우 `true`, 스크립팅 엔진 스크립팅 엔진 자체 나 처리 중인 참조가 하나 이상으로 완벽 하 게 작동 유지 되는 `IDispatch` 는 스크립팅을 사용 하 여 생성 된 JavaScript 개체에 대 한 포인터 엔진입니다. 이 속성 설정 된 경우 `true`를 명시적으로 종료 하거나 사용 하 여 스크립트 엔진을 다시 설정 해야 합니다 [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) 또는 [:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) 메서드. 스크립트 개체에 대 한 마지막 참조의 릴리스를 스크립트 엔진을 종료합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>요구 사항  
 Activscp.idl와 함께 설치 된 버전에만이 속성이 표시 [!INCLUDE[win8](../../javascript/includes/win8-md.md)], KB 2707082에서 Internet Explorer 8을 사용 하 여 [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], 또는에서 Internet Explorer 9 용 KB 2722913 [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] 또는 [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)]합니다.