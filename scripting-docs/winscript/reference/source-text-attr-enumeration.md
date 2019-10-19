---
title: SOURCE_TEXT_ATTR 열거형 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dd0bbf08b6ddfdcfbffa494fdda9842004839b0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572997"
---
# <a name="source_text_attr-enumeration"></a>SOURCE_TEXT_ATTR 열거형
소스 텍스트의 단일 문자 특성을 설명합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>멤버  
  
|멤버|값|설명|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|문자는 언어 키워드의 일부입니다. 예를 들어 VBScript 키워드 `While` 합니다.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|문자는 주석 블록의 일부입니다.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|문자는 컴파일된 언어 소스 텍스트의 일부가 아닙니다. 예를 들어 스크립트 블록을 둘러싼 HTML이 있습니다.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|문자는 언어 연산자의 일부입니다. 예를 들어, 산술 연산자는를 **+** 합니다.|  
|SOURCETEXT_ATTR_NUMBER|0x0010|문자는 언어 숫자 상수의 일부입니다.  예를 들어 상수 3.14159입니다.|  
|SOURCETEXT_ATTR_STRING|0x0020|문자는 언어 문자열 상수의 일부입니다. 예를 들어 문자열 "Hello World"입니다.|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|문자는 함수 블록의 시작을 나타냅니다.|  
  
## <a name="remarks"></a>주의  
 일반적으로 `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes` 및 `IActiveScriptDebug::GetScriptTextAttributes` 메서드는 다음과 같은 경우를 제외 하 고 문자 당 하나의 텍스트 특성을 반환 합니다.  
  
- GETATTRTYPE_DEPSCAN 플래그가 설정 되었습니다 .이 경우 메서드는 SOURCETEXT_ATTR_IDENTIFIER 및 SOURCETEXT_ATTR_MEMBERLOOKUP 플래그를 반환할 수 있습니다.  
  
- GETATTRFLAG_THIS 플래그가 설정 되었습니다 .이 경우 메서드는 SOURCETEXT_ATTR_THIS 플래그를 반환할 수 있습니다.  
  
- GETATTRFLAG_HUMANTEXT 플래그가 설정 되었습니다 .이 경우 메서드는 SOURCETEXT_ATTR_HUMANTEXT 플래그를 반환할 수 있습니다.  
  
## <a name="see-also"></a>참조  
 [액티브 스크립트 디버거 상수, 열거형 및 구조체](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)