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
ms.openlocfilehash: 81f64352c15dce233058d49b70e35da7e2238688
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561646"
---
# <a name="iactivescriptparse"></a>IActiveScriptParse
Windows 스크립트 엔진에서 원시 텍스트 코드 스크립틀릿를 스크립트에 추가 하거나 런타임에 식 텍스트를 평가할 수 있도록 허용 하면 `IActiveScriptParse` 인터페이스를 구현 합니다. VBScript와 같이 독립적인 제작 환경이 없는 해석 된 스크립팅 언어의 경우 스크립트 코드를 스크립팅 엔진으로 가져오고 스크립트 조각을 다양 한 개체 이벤트에 연결 하는 대체 메커니즘 (`IPersist*` 이외)을 제공 합니다. .  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptParse::InitNew](../../winscript/reference/iactivescriptparse-initnew.md)|스크립팅 엔진을 초기화 합니다.|  
|[IActiveScriptParse::AddScriptlet](../../winscript/reference/iactivescriptparse-addscriptlet.md)|스크립트에 scriptlet 코드를 추가 합니다.|  
|[IActiveScriptParse::ParseScriptText](../../winscript/reference/iactivescriptparse-parsescripttext.md)|지정 된 코드 scriptlet를 구문 분석 하 여, 이름 공간에 선언을 추가 하 고 코드를 적절 하 게 평가 합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 인터페이스](../../winscript/reference/active-script-interfaces.md)