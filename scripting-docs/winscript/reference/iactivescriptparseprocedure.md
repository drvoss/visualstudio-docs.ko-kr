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
ms.openlocfilehash: c20947a125766547565d99c5762c20e23652da1a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72561677"
---
# <a name="iactivescriptparseprocedure"></a>IActiveScriptParseProcedure
Windows 스크립트 엔진에서 프로시저에 대 한 소스 코드 텍스트를 스크립트에 추가할 수 있는 경우 `IActiveScriptParseProcedure` 인터페이스를 구현 합니다. VBScript와 같이 독립적인 제작 환경이 없는 해석 된 스크립트 언어의 경우에는 네임 스페이스에 스크립트 프로시저를 추가 하는 대체 메커니즘 (`IActiveScriptParse` 또는 `IPersist` *)이 제공 됩니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|||  
|-|-|  
|메서드|설명|  
|[IActiveScriptParseProcedure::ParseProcedureText](../../winscript/reference/iactivescriptparseprocedure-parseproceduretext.md)|지정 된 코드 프로시저를 구문 분석 하 고 네임 스페이스에 프로시저를 추가 합니다.|  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 인터페이스](../../winscript/reference/active-script-interfaces.md)