---
title: IActiveScriptParseProcedure | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptParseProcedure interface
ms.assetid: 741a35bb-5b92-489e-ba8a-a406b42125fc
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ed07ce5ed48abfb377dde5fc4d5dc128d881b4a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009200"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Windows 스크립트 엔진에서 스크립트에 추가 하는 절차에 대 한 소스 코드 텍스트를 허용 하는 경우 구현 된 `IActiveScriptParseProcedure` 인터페이스입니다. VBScript와 같은 독립 없습니다 제작 환경에 있는 해석 된 스크립팅 언어에 대 한 대체 메커니즘을 제공 (이외의 `IActiveScriptParse` 또는 `IPersist`*) 네임 스페이스에 스크립트 프로시저를 추가 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|||  
|-|-|  
|메서드|설명|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|지정 된 코드 프로시저를 구문 분석 하 고 네임 스페이스에는 프로시저를 추가 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 인터페이스](../../winscript/reference/active-script-interfaces.md)