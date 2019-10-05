---
title: IActiveScriptDebug 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptDebug interface
ms.assetid: e3e28cba-ee08-4a52-973a-b74be488c348
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6341b5c3763d6e4c836b3bdc0539552fcbe7f980
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955031"
---
# <a name="iactivescriptdebug-interface"></a>IActiveScriptDebug 인터페이스
디버깅을 지 원하는 스크립트 엔진에 의해 구현 됩니다. 일반적으로 구현 하는 개체를 `IActiveScriptDebug` 구현도 인터페이스는 `IActiveScript` 인터페이스입니다. 이 경우 호출 된 `IActiveScript::QueryInterface` 메서드를 `IActiveScriptDebug` 인터페이스입니다.  
  
 `IActiveScriptDebug` 인터페이스 수단을 제공 합니다.  
  
- 문서 관리를 수행할 스마트 호스트입니다.  
  
- 프로세스 디버그 관리자를 여러 스크립트 엔진의 디버깅을 동기화 합니다.  
  
  상속 된 메서드 외에도 `IUnknown`, `IActiveScriptDebug` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)|스크립트 텍스트는 임의의 블록용 텍스트 특성을 반환합니다.|  
|[IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)|임의의 scriptlet에 대 한 텍스트 특성을 반환합니다.|  
|[IActiveScriptDebug::EnumCodeContextsOfPosition](../../winscript/reference/iactivescriptdebug-enumcodecontextsofposition.md)|위임 `IDebugDocumentContext::EnumCodeContexts`합니다.|