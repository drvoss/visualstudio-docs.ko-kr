---
title: 액티브 스크립트 디버거 인터페이스 | Microsoft 문서
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger interfaces
- activdbg.h
ms.assetid: bf4750b1-4e58-442b-ab56-254e640de61d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed8ff0361396deaaffd46f14ca1fc38869988593
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422456"
---
# <a name="active-script-debugger-interfaces"></a>액티브 스크립트 디버거 인터페이스
activdbg.h 및 activdbg100.h 헤더 파일은 이 섹션에 나열된 인터페이스, 열거형 및 구조를 제공합니다. 이 헤더 파일은 스크립트를 디버깅하기 위한 것입니다.  
  
> [!NOTE]
> `IJSDebug*` 인터페이스 및 `IEnumJsStackFrames` 인터페이스는 스크립트를 사용하여 네이티브 코드를 디버깅하기 위해 먼저 Internet Explorer 11에서 릴리스되었습니다. 이러한 인터페이스에 대한 헤더 파일은 jscript9diag.h입니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 다음 인터페이스는 언어 중립적이고 호스트 중립적인 디버깅을 허용합니다.  
  
- [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
- [IActiveScriptDebug 인터페이스](../../winscript/reference/iactivescriptdebug-interface.md)  
  
- [IActiveScriptErrorDebug 인터페이스](../../winscript/reference/iactivescripterrordebug-interface.md)  
  
- [IActiveScriptErrorDebug110 인터페이스](../../winscript/reference/iactivescripterrordebug110-interface.md)  
  
- [IActiveScriptSiteDebug 인터페이스](../../winscript/reference/iactivescriptsitedebug-interface.md)  
  
- [IActiveScriptSiteDebug32 인터페이스](../../winscript/reference/iactivescriptsitedebug32-interface.md)  
  
- [IActiveScriptSiteDebugEx 인터페이스](../../winscript/reference/iactivescriptsitedebugex-interface.md)  
  
- [IActiveScriptWinRTErrorDebug 인터페이스](../../winscript/reference/iactivescriptwinrterrordebug-interface.md)  
  
- [IApplicationDebugger 인터페이스](../../winscript/reference/iapplicationdebugger-interface.md)  
  
- [IApplicationDebuggerUI 인터페이스](../../winscript/reference/iapplicationdebuggerui-interface.md)  
  
- [IDebugApplication 인터페이스](../../winscript/reference/idebugapplication-interface.md)  
  
- [IDebugApplication110 인터페이스](../../winscript/reference/idebugapplication110-interface.md)  
  
- [IDebugApplicationNode 인터페이스](../../winscript/reference/idebugapplicationnode-interface.md)  
  
- [IDebugApplicationNode100 인터페이스](../../winscript/reference/idebugapplicationnode100-interface.md)  
  
- [IDebugApplicationNodeEvents 인터페이스](../../winscript/reference/idebugapplicationnodeevents-interface.md)  
  
- [IDebugApplicationThread 인터페이스](../../winscript/reference/idebugapplicationthread-interface.md)  
  
- [IDebugApplicationThread110 인터페이스](../../winscript/reference/idebugapplicationthread110-interface.md)  
  
- [IDebugApplicationThreadEvents110 인터페이스](../../winscript/reference/idebugapplicationthreadevents110-interface.md)  
  
- [IDebugAsyncOperation 인터페이스](../../winscript/reference/idebugasyncoperation-interface.md)  
  
- [IDebugAsyncOperationCallBack 인터페이스](../../winscript/reference/idebugasyncoperationcallback-interface.md)  
  
- [IDebugCodeContext 인터페이스](../../winscript/reference/idebugcodecontext-interface.md)  
  
- [IDebugCookie 인터페이스](../../winscript/reference/idebugcookie-interface.md)  
  
- [IDebugDocument 인터페이스](../../winscript/reference/idebugdocument-interface.md)  
  
- [IDebugDocumentContext 인터페이스](../../winscript/reference/idebugdocumentcontext-interface.md)  
  
- [IDebugDocumentHelper 인터페이스](../../winscript/reference/idebugdocumenthelper-interface.md)  
  
- [IDebugDocumentHost 인터페이스](../../winscript/reference/idebugdocumenthost-interface.md)  
  
- [IDebugDocumentInfo 인터페이스](../../winscript/reference/idebugdocumentinfo-interface.md)  
  
- [IDebugDocumentProvider 인터페이스](../../winscript/reference/idebugdocumentprovider-interface.md)  
  
- [IDebugDocumentText 인터페이스](../../winscript/reference/idebugdocumenttext-interface.md)  
  
- [IDebugDocumentTextAuthor 인터페이스](../../winscript/reference/idebugdocumenttextauthor-interface.md)  
  
- [IDebugDocumentTextEvents 인터페이스](../../winscript/reference/idebugdocumenttextevents-interface.md)  
  
- [IDebugDocumentTextExternalAuthor 인터페이스](../../winscript/reference/idebugdocumenttextexternalauthor-interface.md)  
  
- [IDebugExpression 인터페이스](../../winscript/reference/idebugexpression-interface.md)  
  
- [IDebugExpressionCallBack 인터페이스](../../winscript/reference/idebugexpressioncallback-interface.md)  
  
- [IDebugExpressionContext 인터페이스](../../winscript/reference/idebugexpressioncontext-interface.md)  
  
- [IDebugFormatter 인터페이스](../../winscript/reference/idebugformatter-interface.md)  
  
- [IDebugHelper 인터페이스](../../winscript/reference/idebughelper-interface.md)  
  
- [IDebugSessionProvider 인터페이스](../../winscript/reference/idebugsessionprovider-interface.md)  
  
- [IDebugSessionProviderEx 인터페이스](../../winscript/reference/idebugsessionproviderex-interface.md)  
  
- [IDebugStackFrame 인터페이스](../../winscript/reference/idebugstackframe-interface.md)  
  
- [IDebugStackFrameSniffer 인터페이스](../../winscript/reference/idebugstackframesniffer-interface.md)  
  
- [IDebugStackFrameSnifferEx 인터페이스](../../winscript/reference/idebugstackframesnifferex-interface.md)  
  
- [IDebugSyncOperation 인터페이스](../../winscript/reference/idebugsyncoperation-interface.md)  
  
- [IDebugThreadCall 인터페이스](../../winscript/reference/idebugthreadcall-interface.md)  
  
- [IEnumDebugApplicationNodes 인터페이스](../../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  
- [IEnumDebugCodeContexts 인터페이스](../../winscript/reference/ienumdebugcodecontexts-interface.md)  
  
- [IEnumDebugExpressionContexts 인터페이스](../../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  
- [IEnumDebugStackFrames 인터페이스](../../winscript/reference/ienumdebugstackframes-interface.md)  
  
- [IEnumJsStackFrames 인터페이스](../../winscript/reference/ienumjsstackframes-interface.md)  
  
- [IEnumRemoteDebugApplications 인터페이스](../../winscript/reference/ienumremotedebugapplications-interface.md)  
  
- [IEnumRemoteDebugApplicationThreads 인터페이스](../../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  
- [IJsDebug 인터페이스](../../winscript/reference/ijsdebug-interface.md)  
  
- [IJsDebugBreakPoint 인터페이스](../../winscript/reference/ijsdebugbreakpoint-interface.md)  
  
- [IJsDebugDataTarget 인터페이스](../../winscript/reference/ijsdebugdatatarget-interface.md)  
  
- [IJsDebugFrame 인터페이스](../../winscript/reference/ijsdebugframe-interface.md)  
  
- [IJsDebugProcess 인터페이스](../../winscript/reference/ijsdebugprocess-interface.md)  
  
- [IJsDebugProperty 인터페이스](../../winscript/reference/ijsdebugproperty-interface.md)  
  
- [IJsDebugStackWalker 인터페이스](../../winscript/reference/ijsdebugstackwalker-interface.md)  
  
- [IJsEnumDebugProperty 인터페이스](../../winscript/reference/ijsenumdebugproperty-interface.md)  
  
- [IMachineDebugManager 인터페이스](../../winscript/reference/imachinedebugmanager-interface.md)  
  
- [IMachineDebugManagerCookie 인터페이스](../../winscript/reference/imachinedebugmanagercookie-interface.md)  
  
- [IMachineDebugManagerEvents 인터페이스](../../winscript/reference/imachinedebugmanagerevents-interface.md)  
  
- [IProcessDebugManager 인터페이스](../../winscript/reference/iprocessdebugmanager-interface.md)  
  
- [IProvideExpressionContexts 인터페이스](../../winscript/reference/iprovideexpressioncontexts-interface.md)  
  
- [IRemoteDebugApplication 인터페이스](../../winscript/reference/iremotedebugapplication-interface.md)  
  
- [IRemoteDebugApplication110 인터페이스](../../winscript/reference/iremotedebugapplication110-interface.md)  
  
- [IRemoteDebugApplicationEx 인터페이스](../../winscript/reference/iremotedebugapplicationex-interface.md)  
  
- [IRemoteDebugApplicationEvents 인터페이스](../../winscript/reference/iremotedebugapplicationevents-interface.md)  
  
- [IRemoteDebugApplicationThread 인터페이스](../../winscript/reference/iremotedebugapplicationthread-interface.md)  
  
- [IRemoteDebugApplicationThreadEx 인터페이스](../../winscript/reference/iremotedebugapplicationthreadex-interface.md)  
  
- [ISetNextStatement 인터페이스](../../winscript/reference/isetnextstatement-interface.md)  
  
- [ISimpleConnectionPoint 인터페이스](../../winscript/reference/isimpleconnectionpoint-interface.md)  
  
- [IWebAppDiagnosticsSetup 인터페이스](../../winscript/reference/iwebappdiagnosticssetup-interface.md)  
  
- [IWebAppDiagnosticsObjectInitialization 인터페이스](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md)  
  
  다음 섹션에서는 디버깅에 사용되는 상수, 열거형 및 구조를 나열합니다.  
  
- [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)  
  
## <a name="see-also"></a>참고 항목  
 [액티브 스크립트 디버깅 개요](../../winscript/active-script-debugging-overview.md)