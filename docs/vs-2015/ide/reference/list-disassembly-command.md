---
title: 디스어셈블리 목록 표시 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listdisassembly
helpviewer_keywords:
- Debug.ListDisassembly command
- list disassembly command
ms.assetid: eb363e35-e86a-4121-966f-991210c27e2a
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d361e5231d72df81fae164818bbe8341442c9f89
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199179"
---
# <a name="list-disassembly-command"></a>디스어셈블리 목록 표시 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

디버그 프로세스를 시작하고 오류 처리 방식을 지정할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
Debug.ListDisassembly [/count:number] [/endaddress:expression]  
[/codebytes:yes|no] [/source:yes|no] [/symbolnames:yes|no]  
[/linenumbers:yes|no]  
```  
  
## <a name="switches"></a>스위치  
 각 스위치는 전체 양식 및 약식을 사용하여 호출될 수 있습니다.  
  
 /count: `number` [또는] /c: `number` [또는] /length: `number` [또는] /l: `number`  
 선택 사항입니다. 표시할 지침의 수입니다. 기본값은 8입니다.  
  
 /endaddress: `expression` [또는] /e: `expression`  
 선택 사항입니다. 디스어셈블리를 중지할 주소입니다.  
  
 /codebytes:`yes`&#124;`no` [또는] /bytes:`yes`&#124;`no` [또는] /b:`yes`&#124;`no`  
 선택 사항입니다. 코드 바이트를 표시할지를 나타냅니다. 기본값은 `no`여야 합니다.  
  
 /source:`yes`&#124;`no` [또는] /s:`yes`&#124;`no`  
 선택 사항입니다. 소스 코드를 표시할지를 나타냅니다. 기본값은 `no`여야 합니다.  
  
 /symbolnames:`yes`&#124;`no` [또는] /names:`yes`&#124;`no` [또는] /n:`yes`&#124;`no`  
 선택 사항입니다. 기호 이름을 표시할지를 나타냅니다. 기본값은 `yes`여야 합니다.  
  
 [/linenumbers:`yes`&#124;`no`]  
 선택 사항입니다. 소스 코드와 연결된 줄 번호를 볼 수 있도록 합니다. /source 스위치는 /linenumbers 스위치를 사용하는 `yes`의 값이 있어야 합니다.  
  
## <a name="example"></a>예  
  
```  
>Debug.ListDisassembly  
```  
  
## <a name="see-also"></a>참고 항목  
 [호출 스택 목록 표시 명령](../../ide/reference/list-call-stack-command.md)   
 [스레드 목록 표시 명령](../../ide/reference/list-threads-command.md)   
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)   
 [명령 창](../../ide/reference/command-window.md)   
 [찾기/명령 상자](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
