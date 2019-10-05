---
title: IActiveScriptErrorDebug 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug interface
ms.assetid: e5d50427-c033-4138-ac6e-3b2dfb3b750a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 936770859d3bdfe81c84245d32ae63346b142a01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63009534"
---
# <a name="iactivescripterrordebug-interface"></a>IActiveScriptErrorDebug 인터페이스
컴파일 타임 오류 및 런타임 예외에 대 한 문서 컨텍스트 정보를 제공 합니다. `IActiveScriptError::QueryInterface` 메서드를 지원 합니다 `IActiveScriptErrorDebug` 인터페이스입니다.  
  
 상속 된 메서드 외에도 `IActiveScriptError`, `IActiveScriptErrorDebug` 인터페이스는 다음 메서드를 노출 합니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScriptErrorDebug::GetDocumentContext](../../winscript/reference/iactivescripterrordebug-getdocumentcontext.md)|이 오류에 대 한 문서 컨텍스트를 제공합니다.|  
|[IActiveScriptErrorDebug::GetStackFrame](../../winscript/reference/iactivescripterrordebug-getstackframe.md)|런타임 오류에 적용 되는 스택 프레임을 제공 합니다.|