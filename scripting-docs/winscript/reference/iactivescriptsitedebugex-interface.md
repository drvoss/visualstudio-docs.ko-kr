---
title: IActiveScriptSiteDebugEx 인터페이스 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 605505d101611dfe39835671b042852eab5ca9cb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992382"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx 인터페이스

와 함께이 인터페이스를 구현 합니다 `IActiveScriptSiteDebug` 응용 프로그램에서 런타임 오류 알림을 받고 필요에 따라 디버깅을 위해 응용 프로그램에 연결 해야 하는 호스트를 작성 하는 경우 인터페이스. 프로세스 디버그 관리자를 통해 알림을 제공 `IActiveScriptDebug` 컴퓨터에서 발견 되는 Just In Time 스크립트 디버거에 면 합니다. PDM 제공를 통해 알림을 찾을 수 없는 Just In Time 스크립트 디버거에 하는 경우는 `IActiveScriptDebugEx` 대신 합니다.

런타임 오류에 대 한 알림을 가져오려면 호스트 처리 해야 `ActiveScriptSiteDebug::OnScriptErrorDebug`합니다. 사용자 작업에 따라 결정할 수 있습니다 아니면 반환이 고 내부 디버거를 연결 하는 OnScriptErrorDebug 디버거의 시작 반환 `pfEnterDebugger` 매개 변수입니다.

## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드

|메서드|설명|
|------------|-----------------|
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|프로세스 디버그 관리자 때 스크립트에서 런타임 오류에 대 한 호스트는 외부 Just-in-time 디버거를 찾지 못하면 알립니다.|