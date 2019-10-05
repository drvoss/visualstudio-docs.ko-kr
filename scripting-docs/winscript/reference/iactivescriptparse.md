---
title: IActiveScriptParse | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParse interface
ms.assetid: 8c967d70-f582-4f64-9e79-49f40c4dcb7c
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a987b4be3430f2ed8b0562f41b51a94797f96dc4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009340"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Windows 스크립트 엔진을 스크립트에 추가 될 원시 텍스트 코드 스크립틀릿을 사용 하면 정보나 실행된 시간에 계산할 식 텍스트를 구현 하는지는 `IActiveScriptParse` 인터페이스입니다. VBScript와 같은 독립 없습니다 제작 환경에 있는 해석 된 스크립팅 언어에 대 한 대체 메커니즘을 제공 (이외의 `IPersist*`) 스크립팅 엔진에 스크립트 코드를 가져오려면 및 스크립트 조각 다양 한 개체에 연결 하려면 이벤트입니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|스크립팅 엔진을 초기화합니다.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|스크립트에 코드 scriptlet을 추가 합니다.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|네임 스페이스에 선언을 추가 하 고 적절 하 게 코드를 평가 주어진된 코드 스크립트릿 구문 분석 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 인터페이스](../../winscript/reference/active-script-interfaces.md)