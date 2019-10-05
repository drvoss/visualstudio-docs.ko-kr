---
title: 스레드 목록 표시 명령 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 90aff3fb3d3cbb596708bde1db8ff171198a5a60
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199113"
---
# <a name="list-threads-command"></a>스레드 목록 표시 명령
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

현재 프로그램의 스레드 목록을 표시합니다.  
  
## <a name="syntax"></a>구문  
  
```  
Debug.ListThreads [index]  
```  
  
## <a name="arguments"></a>인수  
 `index`  
 선택 사항입니다. 해당 인덱스별로 현재 스레드가 될 스레드를 선택합니다.  
  
## <a name="remarks"></a>설명  
 지정하는 경우 `index` 인수는 현재 스레드로 지정된 스레드를 표시합니다. 별표(*)는 현재 스레드 옆에 있는 목록에 표시됩니다.  
  
## <a name="example"></a>예  
  
```  
>Debug.ListThreads   
```  
  
## <a name="see-also"></a>참고 항목  
 [호출 스택 목록 표시 명령](../../ide/reference/list-call-stack-command.md)   
 [디스어셈블리 목록 표시 명령](../../ide/reference/list-disassembly-command.md)   
 [Visual Studio 명령](../../ide/reference/visual-studio-commands.md)   
 [명령 창](../../ide/reference/command-window.md)   
 [찾기/명령 상자](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
