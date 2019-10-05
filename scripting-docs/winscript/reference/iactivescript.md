---
title: IActiveScript | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b7e3a0172a798eab9a743f446dff3d339a785b2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436077"
---
# <a name="iactivescript"></a>IActiveScript
스크립팅 엔진을 초기화 하는 데 필요한 메서드를 제공 합니다. 스크립팅 엔진 구현 해야 합니다는 `IActiveScript` 인터페이스입니다.  
  
## <a name="methods-in-vtable-order"></a>Vtable 순서의 메서드  
  
|메서드|설명|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|스크립팅 엔진에 알립니다 합니다 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 호스트에서 제공 되는 사이트입니다.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Windows 스크립트 엔진을 사용 하 여 연결 된 사이트 개체를 검색 합니다.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|스크립팅 엔진의 지정 된 상태로 둡니다.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|스크립팅 엔진의 현재 상태를 검색합니다.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|스크립팅 엔진이 현재 로드 된 스크립트를 중단, 해당 상태가 손실 및 다른 개체를 따라서 닫힌된 상태를 입력 해야 하는 모든 인터페이스 포인터를 해제 합니다.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|스크립팅 엔진의 네임 스페이스에는 루트 수준 항목의 이름을 추가합니다.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|스크립트에 대 한 네임 스페이스에 형식 라이브러리를 추가합니다.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|검색 된 `IDispatch` 실행 중인 스크립트에 대 한 인터페이스입니다.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|현재 실행 중인 스레드에 대 한 스크립팅 엔진 정의 식별자를 검색합니다.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|지정 된 Microsoft Win32 스레드와 연결 된 스레드에 대 한 스크립팅 엔진 정의 식별자를 검색 합니다.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|스크립트 스레드의 현재 상태를 검색합니다.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|실행 중인 스크립트 스레드 실행을 중단합니다.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|현재 스크립팅 엔진 (빼기 모든 현재 실행 상태)를 현재 스레드에서 사이트가 있는 로드 된 스크립팅 엔진 반환을 복제 합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [Windows 스크립트 인터페이스 참조](../../winscript/reference/windows-script-interfaces-reference.md)