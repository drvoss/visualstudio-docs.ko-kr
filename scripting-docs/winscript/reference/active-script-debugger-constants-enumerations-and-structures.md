---
title: 액티브 스크립트 디버거 상수, 열거형 및 구조체 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger structures
- Active Script Debugger enumerations
- Active Script Debugger constants
ms.assetid: b80b9207-fb19-4ee2-85fb-41f8c26e7706
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b287001371b80612a2b09a9672e59aff51309cc9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62997332"
---
# <a name="active-script-debugger-constants-enumerations-and-structures"></a>액티브 스크립트 디버거 상수, 열거형 및 구조체
다음 상수, 열거형 및 구조체는 활성 디버깅 인터페이스에서 사용됩니다.  
  
## <a name="constants-enumerations-and-structures"></a>상수, 열거형 및 구조체  
  
|상수|설명|  
|---------------|-----------------|  
|[APPBREAKFLAGS 상수](../../winscript/reference/appbreakflags-enumeration.md)|현재 애플리케이션 및 스레드에 대한 디버그 상태를 나타냅니다.|  
|[DEBUG_TEXT 상수](../../winscript/reference/debug-text-constants.md)|옵션 플래그를 사용 하는 동안 [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md)합니다.|  
|[TEXT_DOC_ATTR 상수](../../winscript/reference/text-doc-attr-constants.md)|문서의 특성을 설명합니다.|  
  
|열거형|설명|  
|------------------|-----------------|  
|[APPBREAKFLAGS 상수](../../winscript/reference/appbreakflags-enumeration.md)|현재 애플리케이션 및 스레드에 대한 디버그 상태를 나타냅니다.|  
|[APPLICATION_NODE_EVENT_FILTER 열거형](../../winscript/reference/application-node-event-filter-enumeration.md)|필터를 사용하여 제외할 노드를 나타냅니다.|  
|[BREAKPOINT_STATE 열거형](../../winscript/reference/breakpoint-state-enumeration.md)|중단점의 상태를 나타냅니다.|  
|[BREAKREASON 열거형](../../winscript/reference/breakreason-enumeration.md)|중단된 원인을 나타냅니다.|  
|[BREAKRESUMEACTION 열거형](../../winscript/reference/breakresumeaction-enumeration.md)|중단점에서 계속하는 방법을 설명합니다.|  
|[DOCUMENTNAMETYPE 열거형](../../winscript/reference/documentnametype-enumeration.md)|문서에 대한 가져올 유형을 설명합니다.|  
|[ERRORRESUMEACTION 열거형](../../winscript/reference/errorresumeaction-enumeration.md)|런타임 오류에서 계속 진행하는 방법을 설명합니다.|  
|[JS_PROPERTY_ATTRIBUTES 열거형](../../winscript/reference/js-property-attributes-enumeration.md)|속성의 특성을 나타냅니다.|  
|[JS_PROPERTY_MEMBERS 열거형](../../winscript/reference/js-property-members-enumeration.md)|개체의 멤버에 대한 요청에 반환할 정보의 유형을 지정하는 플래그입니다.|  
|[JsDebugReadMemoryFlags 열거형](../../winscript/reference/jsdebugreadmemoryflags-enumeration.md)|메모리를 읽을 때의 동작을 지정하는 플래그입니다.|  
|[SCRIPT_DEBUGGER_OPTIONS 열거형](../../winscript/reference/script-debugger-options-enumeration.md)|연결된 디버거에 적용하는 기능 또는 옵션의 집합을 나타냅니다.|  
|[SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND 열거형](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)|Throw된 예외의 종류를 표시합니다.|  
|[SOURCE_TEXT_ATTR 상수](../../winscript/reference/source-text-attr-enumeration.md)|소스 텍스트의 단일 문자 특성을 설명합니다.|  
  
|구조체|설명|  
|----------------|-----------------|  
|[DebugStackFrameDescriptor 구조체](../../winscript/reference/debugstackframedescriptor-structure.md)|스택 프레임을 열거하고 출력은 동일한 스레드에서 여러 열거자에 병합합니다.|  
|[JS_NATIVE_FRAME 구조체](../../winscript/reference/js-native-frame-structure.md)|스택 프레임을 나타냅니다.|  
|[JsDebugPropertyInfo 구조체](../../winscript/reference/jsdebugpropertyinfo-structure.md)|속성에 대한 정보를 나타냅니다.|  
|[TEXT_DOCUMENT_ARRAY 구조체](../../winscript/reference/text-document-array-structure.md)|문서 집합을 제공합니다.|