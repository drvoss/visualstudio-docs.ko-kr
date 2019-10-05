---
title: IActiveScriptParse32 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c39c14aa-beb7-4eca-8b8c-2181da1c2e3e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: 9f44239b4e423588b8455b93b87e4084a9c7d1c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009323"
---
# <a name="iactivescriptparse32"></a>IActiveScriptParse32
Windows 스크립트 엔진을 스크립트에 추가 될 원시 텍스트 코드 스크립틀릿을 사용 하면 정보나 실행된 시간에 계산할 식 텍스트를 구현 하는지는 `IActiveScriptParse32` 인터페이스입니다. VBScript와 같은 독립 없습니다 제작 환경에 있는 해석 된 스크립팅 언어에 대 한 대체 메커니즘을 제공 (이외의 `IPersist*`) 스크립팅 엔진에 스크립트 코드를 가져오려면 및 스크립트 조각 다양 한 개체에 연결 하려면 이벤트입니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptParse32::AddScriptlet](../../winscript/reference/iactivescriptparse32-addscriptlet.md)|스크립트에 코드 scriptlet을 추가 합니다.|  
|[IActiveScriptParse32::InitNew](../../winscript/reference/iactivescriptparse32-initnew.md)|스크립팅 엔진을 초기화합니다.|  
|[IActiveScriptParse32::ParseScriptText](../../winscript/reference/iactivescriptparse32-parsescripttext.md)|네임 스페이스에 선언을 추가 하 고 적절 하 게 코드를 평가 주어진된 코드 스크립트릿 구문 분석 합니다.|